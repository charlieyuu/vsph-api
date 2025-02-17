# 用户模块

## 1. 用户注册

- 接口路径：`/api/user/register`
- 请求方法： `POST`
- 请求参数：
```json
{
  "user_phone": "用户手机号",
  "user_code": "用户验证码",
  "emergency_phone": "紧急联系人手机号",
  "emergency_code": "紧急联系人验证码",
  "password": "密码"
}
```
- 响应示例：
```json
{
  "code": 200,
  "message": "注册成功"
}
```

## 2. 用户登录
- 接口路径：`/api/user/login`
- 请求方法： `POST`
- 请求参数：
```json
{
  "phone": "手机号",
  "password": "密码",
  "code": "验证码"
}
```
- 参数说明：
    - `password`：密码登录时必填
    - `code`：验证码登录时必填
- 响应示例：
```json
{
  "code": 200,
  "message": "登录成功",
  "data": {
    "access_token": "token",
    "refresh_token": "token"
  }
}
```

## 3. 重置密码
- 接口路径：`/api/user/reset-password`
- 请求方法： `POST`
- 请求参数：
```json
{
  "phone": "手机号",
  "password": "新密码",
  "code": "验证码"
}
```
- 响应示例：
```json
{
  "code": 200,
  "message": "重置成功"
}
```

## 4. 获取用户信息
- 接口路径：`/api/user/info`
- 请求方法： `GET`
- 请求头：`Authorization: Bearer {access_token}`
- 响应示例：
```json
{
  "code": 200,
  "message": "获取成功",
  "data": {
    "user_phone": "用户手机号",
    "emergency_phone": "紧急联系人手机号",
    "avatar": "头像地址",
    "nickname": "昵称"
  }
}
```
- 响应说明：
  - `avatar`：头像地址
  - `nickname`：昵称
  - **用户信息字段待定**

## 5. 获取头像库
- 接口路径：`/api/user/avatars`
- 请求方法： `GET`
- 请求头：`Authorization: Bearer {access_token}`
- 响应示例：
```json
{
  "code": 200,
  "message": "获取成功",
  "data": [
    {
      "id": 1,
      "url": "头像地址"
    },
    {
      "id": 2,
      "url": "头像地址"
    }
  ]
}
```

## 5. 选择头像
- 接口路径：`/api/user/set-avatar`
- 请求方法： `POST`
- 请求头：`Authorization: Bearer {access_token}`
- 请求参数：
```json
{
  "avatar_id": 1
}
```
- 响应示例：
```json
{
  "code": 200,
  "message": "设置成功"
}
```