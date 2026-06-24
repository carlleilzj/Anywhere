# YouTube Anywhere MITM plugin

仓库内文件:
- `Plugins/MITM/youtube_adblock_anywhere_native.amrs` — **Anywhere 原生脚本版（推荐）**
- `Plugins/MITM/youtube_adblock_anywhere.amrs` — 转换版（保留了原始 Surge 脚本）
- `Plugins/MITM/YouTube_surge_module_original.module` — 原始模块内容
- `Plugins/MITM/YouTube_loon_original.yaml` — 旧版原始 override（保留参考）

## 推荐使用
优先使用 `youtube_adblock_anywhere_native.amrs`。

该版本已经改写为 Anywhere 原生支持的 `process(ctx)` 风格脚本，内置实现：
- 拦截 `googlevideo initplayback` 广告请求
- 移除 YouTube JSON 响应中的广告字段
- 移除常见的 Shorts 相关容器节点

## 使用方式
1. 打开 Anywhere
2. 导入 `youtube_adblock_anywhere_native.amrs`
3. 确保 MITM 已启用
4. 信任 Anywhere 根证书
5. 测试 YouTube / YouTube Music

## 说明
原版转换插件仍然保留在仓库中，供对比和参考。  
如果你希望进一步补全字幕翻译、歌词翻译、后台播放设置等高级功能，通常需要继续扩展原生脚本逻辑。

## 当前限制
- 当前原生版本主要处理广告移除和 Shorts 移除
- 并未完整复刻原始 Surge 脚本的全部能力
- 后续可继续迭代增强
