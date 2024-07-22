    /**
     * 监控rabbitmq并推送WS信息给特定用户
     * @param message 带推送信息
     * @param deliveryTag deliveryTag
     * @throws Exception Exception
     */
    @RabbitListener(queues = MqConfig.QUEUE_NAME)
    @RabbitListener(queues = MqConfig.REPORT_QUEUE_NAME)
    public void singleResultWSConsumer(Message message, @Header(AmqpHeaders.DELIVERY_TAG) Long deliveryTag) throws Exception {
        WSSingleResultDTO wsSingleResultDTO = JSON.parseObject(message.getBody(), WSSingleResultDTO.class);
        Action action = Action.SUCCESS;
        try {
            String exeInfoTemp = wsSingleResultDTO.getExeInfo();
            if (CollectionUtils.isEmpty(SESSIONS.get(exeInfoTemp))) {
                // 直接抛出错误，MQ配置了重试3次
                throw new Exception(exeInfoTemp + "WS信息推送失败，重试3次后将被删除");
            }
        } catch (Exception e) {
            logger.error(e.getMessage());
            action = Action.REJECT;
        } finally {
                if (action == Action.SUCCESS) {
                    this.sendMessage(JSON.toJSONString(wsSingleResultDTO.getResultData())
                            , wsSingleResultDTO.getExeInfo());
                }
        }
    }
