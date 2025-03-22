# 认证模块

## 1. 请求手机验证码

- 接口路径：`/api/auth/send-sms-code`
- 请求方法： `POST`
- 请求参数：
```json
{
  "phone_number": "手机号"
}
```
- 响应示例：
```json
{
  "code": 200,
  "message": "验证码发送成功"
}
```

## 2. 刷新token
- 接口说明：当`access_token`过期时，使用`refresh_token`刷新`access_token`，同时返回新的`refresh_token`
- 接口路径：`/api/auth/refresh-access-token`
- 请求方法： `POST`
- 请求参数：
```json
{
  "refresh_token": "token"
}
```
- 响应示例：
```json
{
  "code": 200,
  "message": "刷新成功",
  "data": {
    "access_token": "token",
    "refresh_token": "token"
  }
}
```