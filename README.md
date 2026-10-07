# 我的 LibreTV 影视源

本仓库保存 LibreTV 可导入的点播源清单。

## 订阅地址

https://raw.githubusercontent.com/ljfbin2/tv-sources/main/sources.json

在 LibreTV 中进入 设置 → 源管理 → 数据源订阅，粘贴上述链接并点击订阅。
更新本文件后，在同一订阅条目点击同步。

## 来源与转换

- 来源：[hafrey1/LunaTV-config 的 jin18.json](https://github.com/hafrey1/LunaTV-config/blob/main/jin18.json)
- 获取时间：2026-10-07 23:02 +0800
- 转换后的源数量：28
- 将上游 api_site 中的每项转换为 sources 数组，api 改为 url，保留 name 和 detail，并按完整 URL 去重。
- 本仓库为一次性转换的快照，未配置自动更新任务。
- 数据格式：[LibreTV 数据源文档](https://github.com/LibreSpark/LibreTV/wiki/Data-Sources)

## 验证范围

已验证 JSON 格式、必需字段、HTTP/HTTPS 地址格式、去重和源数量限制。
2026-10-07 曾对豪华、极速、最大、无尽、iKun 的三个关键词搜索及一部影片的播放清单和分片响应头进行抽查。
这不表示本清单全部源或所有影片都可播放，也不表示已在 LibreTV 在线站内完成实播。
源地址和可用性由第三方维护；遇到失效源可在 LibreTV 内停用，或修改本清单后同步。
