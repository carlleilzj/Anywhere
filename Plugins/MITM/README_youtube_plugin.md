# YouTube Anywhere MITM plugin

`youtube_enhance_anywhere.amrs` — 推荐使用

## 错误诊断

之前失败的日志：
```
[YT] init OK - protobuf engine loaded
[YT] process error: undefined is not an object (evaluating 'w.request.url')
```

**根因**：Anywhere 的 JS 运行时是多个请求共享的。原方案用 `globalThis.w` 传参，当多个请求异步交错执行时，`w` 被后面的请求覆盖，导致前一个请求读取到 undefined。

**修复方案**：不再使用 `qr()` / `done()` 路径，绕过 `globalThis.w` 全局变量，直接在 `process()` 中调用：

```
handler = or(url)         → 定位 API 端点
handler.fromBinary(body)  → protobuf 解码
handler.pure()            → 修改（去广告、去按钮、PiP 等）
handler.toBinary()        → protobuf 编码回写
```

所有操作自包含在 handler 实例内部，无共享全局状态。

## 功能

| 功能 | 方式 |
|------|------|
| URL 级广告拦截 | `doubleclick.net` / `googlesyndication` / `initplayback` 等 5 条规则 |
| protobuf 去广告 | 内置 YouTube protobuf 消息定义，完整处理广告字段 |
| 去按钮 | 移除上传 / Shorts / 选段按钮 |
| 去 Shorts shelf | 推荐流去 Shorts 容器 |
| PiP + 后台播放 | player 响应注入字段 |
| 设置开关 | 后台播放设置注入 |

## 日志

导入后可在 Anywhere 日志中搜索 `[YT]`：
- `[YT] init OK - engine ready` → 引擎初始化成功
- `[YT] processed ...` → 某次响应被成功处理
- 如果没有 `[YT]` 日志，说明规则可能没有匹配到请求

## QUIC 说明

YouTube 会使用 QUIC/UDP 绕过 MITM。如要完全拦截，需在路由层对以下域名拒绝 QUIC：

- `googlevideo.com`
- `youtubei.googleapis.com`
