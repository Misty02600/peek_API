# **PeekAPI**

提供当前电脑屏幕截图和录音获取的本地 API

## **API 说明**

| **端点**    | **方法**    | **功能**      | **参数**  | **成功返回**  | **失败返回**  |
|------------|------------|--------------|-----------|--------------|--------------|
| **`/screen`** | `GET` | 获取屏幕截图 | - `r`（截图半径，可选）<br>- `k`（API 密钥，可选） | - `200 OK`，返回 `image/jpeg` 截图 | - `401 Unauthorized`：低模糊度密钥错误<br>- `403 Forbidden`：私密模式<br>- `500 Internal Server Error`：截图失败 |
| **`/record`** | `GET` | 获取最近录音 | 无 | - `200 OK`，返回 `audio/wav` 录音文件 | - `403 Forbidden`：私密模式<br>- `500 Internal Server Error`：录音失败 |
| **`/check`** | `GET/POST` | 检查是否运行 | 无 | - `200 OK` | 无 |


## **配置**

PeekAPI 通过 `config.toml` 进行配置：

```toml
[basic]
is_public = true
api_key = "Imkei"
host = "0.0.0.0"
port = 1920

[screenshot]
radius_threshold = 3
main_screen_only = false

[record]
duration = 20
gain = 20
```

**配置说明**

| **参数**            | **说明**                                      | **默认值**       |
|--------------------|------------------------------------------|---------------|
| **`is_public`**    | 程序启动时默认是否为公开模式               | `true`        |
| **`api_key`**      | 低模糊度下获取截图的密钥                    | `"Imkei"`     |
| **`host`**         | 监听 IP                                    | `"127.0.0.1"` |
| **`port`**         | 监听端口                                  | `1920`        |
| **`radius_threshold`** | 高斯模糊半径阈值，低于该值时调用 `/screen` 需要 `api_key` | `3`           |
| **`main_screen_only`** | 多显示器下是否只截取主显示器               | `false`       |
| **`duration`**     | 录音时间（秒）                            | `20`          |
| **`gain`**        | 音量增益倍数                              | `20`          |


## **许可证**

本项目采用 MIT 许可证。

## **鸣谢**

参考了 [ChieriBot peek API](https://github.com/chinosk6/ChieriBot_peek_API) 的代码
