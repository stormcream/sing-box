### 结构

```json
{
  "type": "fallback",
  "tag": "fallback",
  
  "outbounds": [
    "proxy-a",
    "proxy-b",
    "proxy-c"
  ],
  "url": "",
  "interval": "",
  "idle_timeout": "",
  "interrupt_exist_connections": false
}
```

!!! note ""

    与 `urltest` 不同，`fallback` 不会选择延迟最低的出站。
    它会按配置顺序选择第一个可用出站，且当当前选定的出站超时时，该出站会被标记为不可用，并按顺序选择第一个可用出站。

### 字段

#### outbounds

==必填==

用于测试的出站标签列表。将使用列表中按顺序第一个可用的出站。

#### url

用于测试的链接。默认使用 `https://www.gstatic.com/generate_204`。

#### interval

测试间隔。 默认使用 `3m`。

#### idle_timeout

空闲超时。默认使用 `30m`。

#### interrupt_exist_connections

当选定的出站发生更改时，中断现有连接。

仅入站连接受此设置影响，内部连接将始终被中断。
