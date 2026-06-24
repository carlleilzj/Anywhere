# YouTube Anywhere MITM plugin

## 推荐文件

**`Plugins/MITM/youtube_enhance_anywhere.amrs`**

## 功能

| 功能 | 说明 |
|------|------|
| URL 级别广告请求拦截 | 拦截 `googlevideo initplayback`、`doubleclick`、`googlesyndication` 等广告域名 |
| protobuf 广告字段删除 | 内置 Surge 脚本 protobuf 引擎，处理 YouTube API 响应 |
| 移除按钮 | 移除侧栏的上传/Shorts/选段按钮 |
| 移除 Shorts shelf / reel 覆盖广告 | 清除 feeds 和 Shorts 中的广告 |
| 画中画 / 后台播放 | 在 player 响应中注入相关字段 |
| 歌词/字幕翻译 | 调用 Google Translate |

## 使用方法

1. 导入 → 启用 MITM → 信任证书 → 测试

## 关于 QUIC 协议

YouTube 可能通过 QUIC (UDP) 协议投递广告，而 MITM 只拦截 TCP 连接，QUIC 流量会绕过 MITM。原 Surge 模块也包含了 QUIC 拦截规则：

```
AND,((DOMAIN-SUFFIX,googlevideo.com),(PROTOCOL,QUIC)),REJECT
AND,((DOMAIN-SUFFIX,youtubei.googleapis.com),(PROTOCOL,QUIC)),REJECT
```

如果你在 Anywhere 中设置了路由策略来拦截 QUIC，广告拦截会更彻底。

## 调试

导入本插件后，在 Anywhere 日志中搜索 `[YT]` 可以看到初始化状态和每次请求的处理情况：
- 看到 `[YT] init OK` 表示引擎加载成功
- 看到 `[YT] processed X -> Y bytes` 表示脚本实际改写了响应体
- 没有日志则说明规则可能没匹配到
