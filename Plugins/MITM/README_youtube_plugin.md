# YouTube Anywhere MITM plugin

仓库内文件:

- **`Plugins/MITM/youtube_enhance_anywhere.amrs`** — ✅ 推荐使用，完整的 Anywhere 原生脚本版本
- `Plugins/MITM/youtube_adblock_anywhere.amrs` — 旧的转换版（保留原始 Surge 脚本，可能不兼容）
- `Plugins/MITM/YouTube_surge_module_original.module` — 原始 Surge 模块内容
- `Plugins/MITM/YouTube_loon_original.yaml` — 旧版原始 override（保留参考）

## 功能

当前 `youtube_enhance_anywhere.amrs` 已实现：

**拦截**
- 拦截 `googlevideo initplayback` 广告请求（返回 200 text）

**去广告**
- 删除 `adPlacements` / `adSlots` / `playerAds` / `adBreakParams`
- 删除 Shorts/reel 中的 overlay 广告
- 删除搜索、推荐流中的 Shorts shelf 容器

**去按钮**
- 从侧栏/导航中移除「上传」按钮（FEuploads）
- 从侧栏/导航中移除「Shorts」按钮（FEshorts）  
- 从侧栏/导航中移除「音乐选段」按钮（FEmusic_immersive）

**增强**
- 启用画中画（Picture-in-Picture）
- 启用后台播放（Background Playback）

## 使用方法

1. 打开 Anywhere
2. 导入 `youtube_enhance_anywhere.amrs`
3. 确保 MITM 已启用并信任根证书
4. 测试 YouTube / YouTube Music

## 已知限制

- 当前只处理 JSON 响应体。YouTube 部分接口使用 protobuf（二进制），对应的 body 不会触发脚本处理。
- 字幕翻译、歌词翻译尚未实现（需要外部 HTTP 请求和 Google Translate API）。
- 设置项中新增后台播放开关（category 10135）尚未完整复刻。
