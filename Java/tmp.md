``` java
@PostMapping("api/v1/version/publish")
@ApiOperation(value = "版本发布")
public RestResponse<String> publish(@RequestBody VersionPublishDTO versionPublishDTO) {
    try {
        String token = ShiroUtils.getToken();
        String loginName = ShiroUtils.getCurrentLoginName();
        
        versionService.publish(versionPublishDTO, token, loginName);
        
        return RestResponse.success().build();
    } catch (Exception e) {
        return RestResponse.fail(e.getMessage());
    }
}
```

``` java
@PostMapping("api/v1/version/publish")
@ApiOperation(value = "版本发布")
public RestResponse<String> publish(
    @RequestHeader("Authorization") String token,  // 获取请求头中的Authorization
    @RequestBody VersionPublishDTO versionPublishDTO) {  // 获取请求体中的VersionPublishDTO
    try {
        // 假设ShiroUtils.getToken()和ShiroUtils.getCurrentLoginName()方法依赖于token的值
        // 可以在这里进行适当的改造以确保它们能够正常使用token
        // 例如：
        // ShiroUtils.setToken(token);
        // String loginName = ShiroUtils.getCurrentLoginName();

        // 使用传入的token直接作为参数
        String loginName = ShiroUtils.getCurrentLoginName();
        
        versionService.publish(versionPublishDTO, token, loginName);
        
        return RestResponse.success().build();
    } catch (Exception e) {
        return RestResponse.fail(e.getMessage());
    }
}

```

```

versionService.publish会调用sendHiklinkTextNotice这个方法

public JSONObject sendHiklinkTextNotice(String recipient, String content) {
    JSONObject j = new JSONObject();
    JSONObject emailData = new JSONObject();
    
    emailData.put("biz_type", "special auto test");
    emailData.put("content", content);
    emailData.put("recipient", recipient);
    emailData.put("account", "hice_developer");
    
    j.put("TOKEN", token);
    
    JSONObject resJsonData = this.doPost(
        this.getEndpoint() + this.apiMap.get("SEND_HIKLINK_NOTICE"), 
        j, 
        emailData,
        true
    );
    
    return resJsonData == null ? null : resJsonData.get("data");
}

我想你将这个方法内部做修改， 调用地址变动 和 入参格式变动。要求带上请求头
Authorization:${Token}，请求体
{ "bizCode": "${你们的业务名，比如special-auto-test}", "channel": ["1"], // 1是HikLink消息 "hikLinkSenderUserName": "one", // 站式测试小广播的账号 "msgContext": "f", "hikLinkText": "${要发送的内容}", "msgSender": "${你们的服务标识，unitive-run-report-server}", "receiverNames": ["收件人notes名"] }
```

``` java
@RestController
public class MyController {

    @PostMapping("/api/v1/version/publish")
    public RestResponse<String> publish(@RequestHeader("Authorization") String token,
                                        @RequestBody VersionPublishDTO versionPublishDTO) {
        // 在这里可以使用token变量
        String loginName = ShiroUtils.getCurrentLoginName();
        versionService.publish(versionPublishDTO, token, loginName);
        return RestResponse.success().build();
    }
}

```


``` java
public JSONObject sendHiklinkTextNotice(String recipient, String content) {
    JSONObject j = new JSONObject();
    JSONObject emailData = new JSONObject();
    
    emailData.put("biz_type", "special auto test");
    emailData.put("content", content);
    emailData.put("recipient", recipient);
    emailData.put("account", "hice_developer");
    
    j.put("TOKEN", token);
    
    JSONObject resJsonData = this.doPost(
        this.getEndpoint() + this.apiMap.get("SEND_HIKLINK_NOTICE"), 
        j, 
        emailData,
        true
    );
    
    return resJsonData == null ? null : resJsonData.get("data");
}
```


``` java

public JSONObject sendHiklinkTextNotice(String recipient, String content, String token) {
    JSONObject requestData = new JSONObject();
    JSONArray receiverNames = new JSONArray();
    receiverNames.put(recipient);

    JSONObject msgContext = new JSONObject();
    msgContext.put("hikLinkText", content);

    requestData.put("bizCode", "special-auto-test");
    requestData.put("channel", new JSONArray().put("1")); // 1是HikLink消息
    requestData.put("hikLinkSenderUserName", "one"); // 站式测试小广播的账号
    requestData.put("msgContext", msgContext);
    requestData.put("msgSender", "unitive-run-report-server");
    requestData.put("receiverNames", receiverNames);

    JSONObject headers = new JSONObject();
    headers.put("Authorization", "Bearer " + token);

    JSONObject resJsonData = this.doPostWithHeaders(
        "https://your-new-endpoint-url", // 替换为新的调用地址
        headers,
        requestData
    );

    return resJsonData == null ? null : resJsonData.optJSONObject("data");
}

private JSONObject doPostWithHeaders(String url, JSONObject headers, JSONObject requestData) {
    // 构建HTTP POST请求，设置请求头和请求体，发送请求并返回响应
    // 省略具体实现细节，可以使用HttpClient或其他HTTP库实现
    return null; // 根据实际情况返回响应数据
}


private JSONObject doPostWithHeaders(String url, JSONObject headers, JSONObject requestData) {
    // 构建HTTP POST请求，设置请求头和请求体，发送请求并返回响应
    // 省略具体实现细节，可以使用HttpClient或其他HTTP库实现
    return null; // 根据实际情况返回响应数据
}

```

``` java
public JSONObject sendHiklinkTextNotice(String recipient, String content, String token) {
    JSONObject requestData = new JSONObject();
    JSONArray receiverNames = new JSONArray();
    receiverNames.put(recipient);

    JSONObject msgContext = new JSONObject();
    msgContext.put("hikLinkText", content);

    requestData.put("bizCode", "special-auto-test");
    requestData.put("channel", new JSONArray().put("1")); // 1是HikLink消息
    requestData.put("hikLinkSenderUserName", "one"); // 站式测试小广播的账号
    requestData.put("msgContext", msgContext);
    requestData.put("msgSender", "unitive-run-report-server");
    requestData.put("receiverNames", receiverNames);

    JSONObject headers = new JSONObject();
    headers.put("Authorization", "Bearer " + token);

    JSONObject resJsonData = this.doPostWithHeaders(
        "http://hiktest.hikvision.com.cn/messageCenterPortal/api/v1/message/send", // 新的调用地址
        headers,
        requestData
    );

    return resJsonData == null ? null : resJsonData.optJSONObject("data");
}

private JSONObject doPostWithHeaders(String url, JSONObject headers, JSONObject requestData) {
    try {
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest.Builder requestBuilder = HttpRequest.newBuilder()
            .uri(URI.create(url))
            .POST(HttpRequest.BodyPublishers.ofString(requestData.toString()))
            .header("Content-Type", "application/json");
        
        headers.keys().forEachRemaining(key -> requestBuilder.header(key, headers.getString(key)));
        
        HttpRequest request = requestBuilder.build();
        
        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
        return new JSONObject(response.body());
    } catch (Exception e) {
        e.printStackTrace();
        return null;
    }
}

```