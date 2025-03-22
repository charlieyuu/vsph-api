# 问卷模块

使用阿里云的推送服务，移动端接入 SDK，后端通过调用阿里云的接口向移动端推送问卷填写消息，用户点击后跳转到应用内问卷填写页面。

## 1. 获取当前问卷

- 接口说明：用户进入问卷填写页面时调用该接口获取当前时间段对应的问卷
- 接口路径：`/api/questionnaire/current`
- 请求方法： `GET`
- 请求头：`Authorization: Bearer {access_token}`
- 响应示例：

```json
{
  "code": 200,
  "message": "获取成功",
  "data": {
    "id": 1,
    "title": "问卷标题",
    "description": "问卷描述",
    "questions": [
      {
        "number": 1,
        "required": true,
        "text": "题目文本",
        "placeholder": "请输入答案",
        "type": "text-question"
      },
      {
        "number": 2,
        "required": true,
        "text": "此时此刻，我与朋友们关系密切",
        "min": 1,
        "minLabel": "完全不正确",
        "max": 7,
        "maxLabel": "完全正确",
        "type": "rating-question"
      },
      {
        "number": 3,
        "required": true,
        "text": "自上次评估以后，您有过自杀的想法吗?",
        "type": "single-select-question",
        "options": [
          { "label": "否", "value": 0 },
          {
            "label": "是",
            "value": 1,
            "children": [
              {
                "number": 4,
                "required": true,
                "text": "您产生这些自杀想法的次数有多少？",
                "min": 0,
                "minLabel": "只有一次",
                "max": 4,
                "maxLabel": "一直",
                "type": "rating-question"
              }
            ]
          }
        ]
      },
      {
        "number": 4,
        "fields": ["hour", "minute"],
        "required": true,
        "text": "您昨天晚上上床睡觉的时间",
        "type": "time_question"
      }
    ]
  }
}
```

- 响应说明：
  - `data`中为一次问卷的信息，示例中给出了单选题、评分题、填空题和时间选择题的 json 格式，包括题目嵌套关系，不同类型的题目形式可参考形式可参考http://8.152.200.205/questionnaire/
  - 时间选择题的fields表示需要用户选择的时间段，如例题4中需要用户选择一个包含小时和分钟的时间

## 2. 获取人口学消息问卷（注册时填写）

- 接口说明：用户注册时调用该接口获取人口学消息问卷
- 接口路径：`/api/questionnaire/demographic`
- 请求方法： `GET`
- 请求头：`Authorization: Bearer {access_token}`
- 响应示例同上

## 2. 提交问卷

- 接口说明：用户填写完问卷后调用该接口提交问卷
- 接口路径：`/api/questionnaire/submit`
- 请求方法： `POST`
- 请求头：`Authorization: Bearer {access_token}`
- 请求参数：

```json
{
  "questionnaire_id": 1,
  "answers": [
    {
      "number": 1,
      "value": "答案"
    },
    {
      "number": 2,
      "value": 5
    },
    {
      "number": 3,
      "value": 1
    }
  ]
}
```

- 请求参数说明：
  - 由于所有问题的编号是同一级别的（包括嵌套问题），所以只需要按列表形式提交问题编号和答案即可
  - 对于时间题，答案为yyyy-MM-dd HH:mm:ss，不需要选择的字段默认为0即可，如0000-00-00 20:01:00
- 响应示例：

```json
{
  "code": 200,
  "message": "提交成功"
}
```
