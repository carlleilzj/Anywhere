# YouTube Anywhere MITM plugin (converted from provided module)

仓库内文件:
- 原始模块内容：`Plugins/MITM/YouTube_surge_module_original.module`
- Anywhere 规则集：`Plugins/MITM/youtube_adblock_anywhere.amrs`
- 旧版原始 override（保留参考）：`Plugins/MITM/YouTube_loon_original.yaml`

## 当前状态
已按你提供的模块内容重建了 Anywhere MITM 规则集，并将响应脚本以 base64 嵌入 `.amrs` 文件。

包含内容：
- MITM 域名：`googlevideo.com`、`youtubei.googleapis.com`
- `googlevideo initplayback` 广告请求拦截规则
- 响应脚本规则（来自 GitHub 原始 `youtube.response.js`）

## 使用方式
1. 打开 Anywhere
2. 导入 `youtube_adblock_anywhere.amrs`
3. 确保 MITM 已启用
4. 信任 Anywhere 根证书
5. 测试 YouTube / YouTube Music

## 重要提醒
原始脚本来自 Surge/模块生态，内部使用了 Surge 脚本运行时相关接口（例如脚本宿主对象）。

这意味着：
- `.amrs` 文件现在已可以导入
- 但脚本在 Anywhere 中**不一定能完整运行**
- Anywhere 的 MITM 脚本 API 与 Surge 并不完全一致

如果导入后发现功能不全，下一步通常需要：
- 将脚本改写为 Anywhere 原生支持的 `process(ctx)` 风格
- 或用 Anywhere 的 `Anywhere.json` / `Anywhere.codec.protobuf` 重新实现同样逻辑

## 链接
- `Plugins/MITM/youtube_adblock_anywhere.amrs`
- `Plugins/MITM/YouTube_surge_module_original.module`
