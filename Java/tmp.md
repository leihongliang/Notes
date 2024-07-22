/**
 * 监控rabbitmq并推送WS信息给特定用户
 * @param message 带推送信息
 * @param deliveryTag deliveryTag
 * @param headers 消息头
 * @throws Exception Exception
 */
@RabbitListener(queues = MqConfig.QUEUE_NAME)
@RabbitListener(queues = MqConfig.REPORT_QUEUE_NAME)
public void singleResultWSConsumer(Message message, @Header(AmqpHeaders.DELIVERY_TAG) Long deliveryTag, @Headers Map<String, Object> headers) throws Exception {
    WSSingleResultDTO wsSingleResultDTO = JSON.parseObject(message.getBody(), WSSingleResultDTO.class);
    Action action = Action.SUCCESS;
    int retryCount = 0;

    // 获取重试次数
    if (headers.containsKey("x-death")) {
        List<Map<String, Object>> deaths = (List<Map<String, Object>>) headers.get("x-death");
        if (deaths != null && !deaths.isEmpty()) {
            retryCount = (int) deaths.get(0).get("count");
        }
    }

    try {
        String exeInfoTemp = wsSingleResultDTO.getExeInfo();
        if (CollectionUtils.isEmpty(SESSIONS.get(exeInfoTemp))) {
            if (retryCount >= 2) { // 第三次重试时记录日志
                throw new Exception(exeInfoTemp + "WS信息推送失败，重试3次后将被删除");
            } else {
                throw new Exception(); // 前两次重试不记录详细信息
            }
        }
    } catch (Exception e) {
        if (retryCount >= 2) { // 第三次重试时记录日志
            logger.error(exeInfoTemp + "WS信息推送失败，重试3次后将被删除");
        }
        action = Action.REJECT;
    } finally {
        if (action == Action.SUCCESS) {
            this.sendMessage(JSON.toJSONString(wsSingleResultDTO.getResultData()), wsSingleResultDTO.getExeInfo());
        }
    }
}
