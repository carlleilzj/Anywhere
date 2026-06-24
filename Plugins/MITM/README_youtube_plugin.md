# YouTube Anywhere MITM plugin

## 推荐文件

**`Plugins/MITM/youtube_enhance_anywhere.amrs`**

## 功能清单

| 功能 | 状态 |
|------|------|
| 拦截 googlevideo initplayback 广告请求 | ✅ |
| 移除 adPlacements / adSlots / playerAds | ✅ |
| 移除 Shorts shelf 容器 | ✅ |
| 移除 Shorts/reel overlay 广告 | ✅ |
| 移除「上传」按钮（FEuploads） | ✅ |
| 移除「Shorts」按钮（FEshorts） | ✅ |
| 移除「音乐选段」按钮（FEmusic_immersive） | ✅ |
| 启用画中画（PiP） | ✅ |
| 启用后台播放 | ✅ |
| 歌词翻译（Google Translate） | ✅ |
| 字幕翻译支持 | ✅ |
| 设置页新增后台播放开关 | ✅ |
| protobuf 二进制响应处理 | ❌ |

## 使用方式

1. 打开 Anywhere → 导入 `youtube_enhance_anywhere.amrs`
2. 确保 MITM 已启用并信任根证书
3. 测试 YouTube / YouTube Music

## 仓库文件

- `Plugins/MITM/youtube_enhance_anywhere.amrs` — 完整原生版（推荐）
- `Plugins/MITM/YouTube_surge_module_original.module` — 原始模块
- `Plugins/MITM/youtube_adblock_anywhere_native.amrs` — 旧版原生（仅去广告+去Shorts）
- `Plugins/MITM/youtube_adblock_anywhere.amrs` — 旧版转换（含 Surge 原脚本 base64）
- `Plugins/MITM/YouTube_loon_original.yaml` — 旧版 Stash override
