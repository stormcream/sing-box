### Structure

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

    Unlike `urltest`, `fallback` doesn't select the outbound with the lowest latency.
    It selects the first available outbound in the configured order, and when the selected outbound times out,
    it will be marked unavailable and the first available outbound in the order will be selected.

### Fields

#### outbounds

==Required==

List of outbound tags to test. The first available outbound in the list will be used.

#### url

The URL to test. `https://www.gstatic.com/generate_204` will be used if empty.

#### interval

The test interval. `3m` will be used if empty.

#### idle_timeout

The idle timeout. `30m` will be used if empty.

#### interrupt_exist_connections

Interrupt existing connections when the selected outbound has changed.

Only inbound connections are affected by this setting, internal connections will always be interrupted.
