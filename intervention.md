# 干预模块

同问卷模块，后端通过调用阿里云的接口向移动端推送干预消息，用户点击后跳转到干预页面。

## 1. 获取当前干预方案
- 接口路径：`/api/intervention`
- 请求方法： `GET`
- 请求头：`Authorization: Bearer {access_token}`
- 响应示例：
```json
{
  "code": 200,
  "message": "获取成功",
  "data": {
    "help_hotline": "求助电话",
    "sentence": "干预文本",
    "image": "干预图片",
    "video": "干预视频"
  }
}
```