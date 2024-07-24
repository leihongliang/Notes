    public List<JSONObject> getFailedTop5Script(LocalDate starDateTime, LocalDate endDateTime
            , String projectId, String projectType) {
        List<JSONObject> failScripts = new ArrayList();
        //返回单元是单个script某天执行失败的次数
        List<AccountProjectFailTopFive> accountProjectFailTopFives =
                accountProjectFailTopFiveDao.findAllByProjectIdAndProjectType(projectId, projectType);
        // 在这里对可能出现的（原来是多容器监听结算导致的数据重复问题）ScriptId重复问题进行处理
        Map<String, AccountProjectFailTopFive> accountProjectFailTopFiveNonDuplicate =
                accountProjectFailTopFives.stream()
                        .collect(Collectors.toMap(
                                AccountProjectFailTopFive::getScriptId,
                                Function.identity(),
                                (existing, replacement) -> existing // 如果键冲突，保留现有的值
                        ));
        List<AccountProjectFailTopFive> list = new ArrayList<>(accountProjectFailTopFiveNonDuplicate
                .values());
        accountProjectFailTopFives = list;
        //过滤时间，按scriptID分组
        Map<String, List<AccountProjectFailTopFive>> filterAccountProjectFailTopFives = accountProjectFailTopFives
                .stream()
                .filter(accountProjectFailTopFive -> {
                    LocalDate accountDate = LocalDate.parse(accountProjectFailTopFive.getAccountDate());
                    return ((accountDate.isAfter(starDateTime) || accountDate.isEqual(starDateTime))
                            && (accountDate.isBefore(endDateTime) || accountDate.isEqual(endDateTime)))
                            && accountProjectFailTopFive.getType().equals(StringConsts.FAIL_SCRIPT);
                })
                .collect(Collectors.groupingBy(AccountProjectFailTopFive::getScriptId));
        Map<String, AccountProjectFailTopFive> scriptIdToACC = accountProjectFailTopFives
                .stream()
                .filter(item -> Objects.nonNull(item.getScriptId()))
                .collect(Collectors.toMap(AccountProjectFailTopFive::getScriptId
                        , accountProjectFailTopFive -> accountProjectFailTopFive));


        // 利用 Priority 队列来寻找个数最多的 5 个数据 
        PriorityQueue<Map.Entry<String, Integer>> pq = new PriorityQueue<>(5, (a, b) ->
                Integer.compare(a.getValue(), b.getValue()));

        List<String> brIds = new ArrayList<>();
        for (Map.Entry<String, List<AccountProjectFailTopFive>> entry : filterAccountProjectFailTopFives.entrySet()) {
            Integer count = entry.getValue().stream().mapToInt(AccountProjectFailTopFive::getTotalFailNum).sum();
            if (pq.size() < 5) {
                pq.offer(new AbstractMap.SimpleEntry<>(entry.getKey(), count));
                brIds.addAll(entry
                        .getValue()
                        .stream()
                        .map(AccountProjectFailTopFive::getBatchRecordIdList)
                        .flatMap(List::stream)
                        .collect(Collectors.toList()));
            } else if (count > pq.peek().getValue()) {
                pq.poll();
                pq.offer(new AbstractMap.SimpleEntry<>(entry.getKey(), count));
                brIds.addAll(entry
                        .getValue()
                        .stream()
                        .map(AccountProjectFailTopFive::getBatchRecordIdList)
                        .flatMap(List::stream)
                        .collect(Collectors.toList()));
            }
        }

        // 输出结果 
        List<Map.Entry<String, Integer>> resList = new ArrayList<>(pq);
        Collections.sort(resList, (a, b) -> Integer.compare(b.getValue(), a.getValue()));
        List<String> srIds = resList
                .stream()
                .map(map -> map.getKey())
                .collect(Collectors.toList());
        List<ScriptRecord> scriptRecords = scriptRecordService.getScriptRecordByBatchRecordIdsAndScriptIds(brIds, srIds
                , BaseModel.Fields.id, ScriptRecord.Fields.name, ScriptRecord.Fields.scriptId);
        // 使用HashSet来辅助去重
        Set<String> uniqueSrs = new HashSet<>();
        Map<String, ScriptRecord> idToSr = scriptRecords
                .stream()
                .filter(scriptRecord -> uniqueSrs.add(scriptRecord.getScriptId()))
                .collect(Collectors.toMap(ScriptRecord::getScriptId, scriptRecord -> scriptRecord));

        for (Map.Entry<String, Integer> entry : resList) {
            JSONObject retJsonData = new JSONObject();
            AccountProjectFailTopFive accountProjectFailTopFive = scriptIdToACC.get(entry.getKey());
            retJsonData.put("batchRecordIdList", accountProjectFailTopFive.getBatchRecordIdList());
            retJsonData.put(FAIL_CNT, entry.getValue());
            retJsonData.put("scriptName", idToSr.get(entry.getKey()).getName());
            retJsonData.put(SCRIPT_ID, entry.getKey());
            failScripts.add(retJsonData);
        }

        return failScripts;
    }
