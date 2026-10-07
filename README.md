# 我的 LibreTV 影视源

本仓库保存 LibreTV 可一次导入的 28 个点播源和 2 组直播列表。

## 订阅地址

https://raw.githubusercontent.com/ljfbin2/tv-sources/main/sources.json

在 LibreTV 中进入 设置 → 源管理 → 数据源订阅，粘贴上述链接并点击订阅。
已订阅的用户在同一订阅条目点击“同步”，然后进入顶部“直播”页面选择频道。订阅地址保持不变；需要支持 liveSources 的 LibreTV 版本。

## 来源与转换

- 来源：[hafrey1/LunaTV-config 的 jin18.json](https://github.com/hafrey1/LunaTV-config/blob/main/jin18.json)
- 获取时间：2026-10-07 23:02 +0800
- 转换后的源数量：28
- 将上游 api_site 中的每项转换为 sources 数组，api 改为 url，保留 name 和 detail，并按完整 URL 去重。
- 本仓库为一次性转换的快照，未配置自动更新任务。
- 数据格式：[LibreTV 数据源文档](https://github.com/LibreSpark/LibreTV/wiki/Data-Sources)

## 直播来源

- **国内电视 · IPTV-org**：[频道列表](https://iptv-org.github.io/iptv/countries/cn.m3u) · [维护仓库](https://github.com/iptv-org/iptv)
- **港澳台及海外 · YueChan**：[频道列表](https://raw.githubusercontent.com/YueChan/Live/main/GNTV.m3u) · [维护仓库](https://github.com/YueChan/Live)

直播配置使用 LibreTV 的 liveSources 数组，每项包含 name 和 url。频道内容来自上游 M3U 列表，可能随上游更新而变化，本仓库没有复制频道地址，也未配置自动更新任务。
点播 sources 数组保留原有 28 项。两组直播列表可能包含重复频道，部分频道存在地区、IPv6、格式或时段限制。
格式与使用说明：[LibreTV 直播文档](https://github.com/LibreSpark/LibreTV/wiki/Live-IPTV)。

## 验证范围

已验证 JSON 格式、必需字段、HTTP/HTTPS 地址格式、去重和源数量限制。
2026-10-07 曾对豪华、极速、最大、无尽、iKun 的三个关键词搜索及一部影片的播放清单和分片响应头进行抽查。
这不表示本清单全部源或所有影片都可播放，也不表示已在 LibreTV 在线站内完成实播。
源地址和可用性由第三方维护；遇到失效源可在 LibreTV 内停用，或修改本清单后同步。

### 直播抽查（2026-10-07）

两组 M3U 列表均可读取且格式有效。抽查 CCTV-1、CCTV-13、浙江国际、TVBS 新闻、三立新闻、CNA、NHK World 共 7 个频道，播放清单可读取，实际媒体分片的部分读取请求均返回 HTTP 206。
这只证明测试时清单与分片可访问，不能证明持续播放稳定、全部频道可用或浏览器兼容；尚未完成 LibreTV 网页实际播放验收。遇到不可用频道，可在直播页使用“测活”和“仅可用”筛选。
