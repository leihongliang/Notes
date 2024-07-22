    @OnOpen
    public void onOpen(Session session, @PathParam("exeInfo") String exeInfo) {
        this.session=session;
        if (StringUtils.isEmpty(exeInfo)) {
            logger.error("未传WS信息定向推送的相关信息");
        }
        this.exeInfo = exeInfo;
        addOnlineCount();
        SESSIONS.computeIfAbsent(exeInfo, s -> new CopyOnWriteArrayList<>()).add(this);
        logger.info("websocket连接成功,总数为:{}", getOnlineCount());
    }
