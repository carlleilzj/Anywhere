# YouTube Anywhere MITM plugin

## 推荐文件

**`Plugins/MITM/youtube_enhance_anywhere.amrs`**

## 功能

✅ 本插件已嵌入原始 Surge 脚本的 protobuf 引擎，可直接处理 YouTube API 的二进制响应。

| 功能 | 说明 |
|------|------|
| 拦截 `googlevideo initplayback` 广告请求 | 返回 200 空响应 |
| protobuf 去广告 | 完整处理 YouTube API 二进制 protobuf 响应，删除广告字段 |
| 移除上传/Shorts/选段按钮 | 从侧栏导航中移除 FEuploads / FEshorts / FEmusic_immersive |
| 移除 Shorts shelf | 从推荐流和搜索结果中移除 Shorts 容器 |
| 移除 reel overlay 广告 | 清除 Shorts 中的覆盖层广告 |
| 启用画中画 / 后台播放 | 在 player 响应中注入相关字段 |
| 歌词翻译 | 调用 Google Translate 翻译歌词 |
| 字幕翻译 | 在播放器中注入翻译字幕轨道 |
| 后台播放设置 | 在设置页注入后台播放开关 |

## 使用方式

1. 打开 Anywhere
2. 导入 `youtube_enhance_anywhere.amrs`
3. 确保 MITM 已启用并信任根证书
4. 测试 YouTube / YouTube Music

## 实现原理

- 插件嵌入了原始 Surge 脚本的完整 protobuf 运行时和 YouTube 消息定义
- 通过 Anywhere 适配层（shim）将 Surge API 映射为 Anywhere 原生 API
- 首次调用时初始化 Surge 兼容层，之后每次请求直接在适配环境上处理
- init 会打印 `[YT]` 日志，可在 Anywhere 日志中查看是否正常加载
