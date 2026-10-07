# 影视源订阅（LibreTV / EchoTV）

本仓库提供 LibreTV 与 EchoTV 两种订阅格式。LibreTV 包含 28 个点播源和 2 组直播列表；EchoTV 包含全部 28 个点播源和 11 个精选直播频道。

## LibreTV 订阅地址

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

直播配置使用 LibreTV 的 liveSources 数组，每项包含 name 和 url。频道内容来自上游 M3U 列表，可能随上游更新而变化，LibreTV 订阅直接引用上游列表，未配置自动更新任务；EchoTV 使用另行整理的频道入口快照。
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

## EchoTV 安卓订阅（28 个点播源）

[EchoTV 完整订阅](https://raw.githubusercontent.com/ljfbin2/tv-sources/main/echotv.json)

在 EchoTV v1.0.6 中进入“设置 → 配置同步 → 订阅管理 → 添加订阅”，名称填写“龙哥影视源”，URL 填上面的链接，保存并同步。导入后可在源管理中核对 28 个点播源；直播包含“直连精选 · 11频道”。

- 按用户要求保留全部 28 个点播源，包括抽查失败或播放线路重复的源，没有按测试结果删减。
- 格式转换为 EchoTV 的 api_site / lives 对象。name、detail 保留，url 转为 api；EchoTV 不使用 detail 抓取网页播放地址。
- 百度云、艾旦的转发包装 URL 改为对应的原始 AppleCMS API，避免 EchoTV 拼接查询参数时不兼容；两项均保留，原始 API 搜索请求已验证。
- [直播频道列表](https://raw.githubusercontent.com/ljfbin2/tv-sources/main/echo-live.m3u)是从上方两组公开列表抽取的固定入口快照，包含央视 1/2/9/13、浙江国际、浙江新闻、TVBS、东森、三立、CNA、NHK World。未配置自动更新。
- 格式依据：[EchoTV v1.0.6 订阅解析](https://github.com/hoowhoami/EchoTV/blob/v1.0.6/lib/services/subscription_service.dart)。

### EchoTV 核查范围（2026-10-08）

使用本机直连（requests trust_env=False），按 EchoTV 请求与选线方式抽查了 28 个点播接口；其中 9 个通过电影、剧集两组清单与分片可访问性检查，结果没有作为删除依据。其他源仍可能有可播放内容。
11 个直播频道通过本机直连的 HLS 清单和少量分片字节检查。以上不代表安卓实播、画面声音、持续速度或全部内容已通过验收；不同运营商的连接结果可能不同。

