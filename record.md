﻿# 录音模块

按当前需求，APP 内用户填写完问卷提交后跳转到录音页面，录制后上传音频文件到服务器。

## 1. 获取录制题目

- 接口说明：可先按给定的来，预留接口方便后续调整
- 接口路径：`/api/record/theme?questionnaire_id={questionnaire_id}`
- 请求方法： `GET`
- 请求头：`Authorization: Bearer {access_token}`
- 响应示例：

```json
{
  "code": 200,
  "message": "获取成功",
  "data": [
    {
      "question_number": 1,
      "question_type": "text_question",
      "theme": "请简单描述一下自上次评估后到现在，你感觉怎么样？有发生什么事情吗？可以描述一下。作答时间不少于1分钟。"
    },
    {
      "question_number": 2,
      "question_type": "text_question",
      "theme": "请简单描述一下自上次评估后到现在，你感觉怎么样？有发生什么事情吗？可以描述一下。作答时间不少于1分钟。"
    },
    ...
  ]
}
```

## 2. 上传录音文件

- 接口路径：`/api/record/upload`
- 请求方法： `POST`
- 请求头：`Authorization: Bearer {access_token}; Content-Type: multipart/form-data`
- 请求参数：
  - `questionnaire_id`: 问卷 ID
  - `question_number`: 问题序号
  - `file`: 录音文件
- 响应示例：

```json
{
  "code": 200,
  "message": "上传成功"
}
```
