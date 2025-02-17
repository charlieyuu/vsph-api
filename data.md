# 数据采集模块

## 1. 上传用户数据
- 接口说明：每10分钟上传一次用户数据
- 接口路径：`/api/data/collect`
- 请求方法： `POST`
- 请求头：`Authorization: Bearer {access_token}`
- 请求参数：
```json
{
  "screen_time": 120,
  "steps": 1000,
  "call_count": 10,
  "sms_count": 20,
  "gps": [
    {
      "latitude": 30.123456,
      "longitude": 120.123456,
      "timestamp": 1612345678
    },
    {
      "latitude": 30.123456,
      "longitude": 120.123456,
      "timestamp": 1612345678
    }
  ],
  "timestamp": 1612345678
}
```
- 请求参数说明：
  - `screen_time`：屏幕使用时长（单位：秒）
  - `steps`：步数
  - `call_count`：通话次数
  - `sms_count`：短信次数
  - `gps`：GPS数据
    - `latitude`：纬度
    - `longitude`：经度
    - `timestamp`：时间戳
  - `timestamp`：数据时间戳
- 响应示例：
```json
{
  "code": 200,
  "message": "上传成功"
}
```