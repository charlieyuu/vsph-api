# 移动推送说明

## 1. 问卷推送

在推送的额外参数中携带当次推送对应的问卷Id，部分参数如下所示：
```json
{
    "Title" = "问卷调查",
    "Body" = "您有新的问卷需要填写",
    "AndroidNotificationChannel" = "DEFAULT",
    "AndroidOpenType" = "APPLICATION",
    "AndroidExtParameters" = "{\"questionnaire_id\":\"" + questionnaireId + "\"}",
}
```
可通过以下接口发起一次问卷全推，测试推送功能的可用性：
- 接口路径：`/api/push/questionnaire`
- 请求方法： `POST`
- 响应示例：
```json
{
  "code": 200,
  "message": null,
  "data": null
}
```

## 2. 干预推送

同样地，在推送的额外参数中携带当次推送对应的干预Id，部分参数如下所示：
```json
{
    "Title" = "干预通知",
    "Body" = "您有新的干预信息",
    "AndroidNotificationChannel" = "DEFAULT",
    "AndroidOpenType" = "APPLICATION",
    "AndroidExtParameters" = "{\"intervention_id\":\"" + interventionId + "\"}",
}
```
可通过以下接口发起一次干预全推，测试推送功能的可用性：
- 接口路径：`/api/push/intervention`
- 请求方法： `POST`
- 响应示例：
```json
{
  "code": 200,
  "message": null,
  "data": null
}
```