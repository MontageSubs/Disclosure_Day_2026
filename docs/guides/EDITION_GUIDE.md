# 版次命名指南

一个版次对应一份独立时间轴：剪辑版本、片源或区域任一不同，即建立独立目录，互不影响、互不覆盖。

## 触发方式

通过 [Actions](../../../../actions/workflows/add-edition.yml) 中的 **新增 Edition (Add Edition)** workflow 手动触发（首次初始化时也会一并要求填写），需在表单中提供以下三项之一（**三选一，必选**）：

- **WEB** —— 片源为网络流媒体版本
- **BluRay** —— 片源为蓝光版本
- **自定义来源标识**（文本框）—— 上方两项均不适用时，在此填写完整来源标识；若已勾选 WEB 或 BluRay，此处可选填区域 / 剪辑版本后缀

## 目录名生成规则

| 场景 | 目录名 |
| :--- | :--- |
| 仅勾选 WEB | `web` |
| 仅勾选 BluRay | `bluray` |
| 勾选 WEB + 填写 `uk` | `web-uk` |
| 勾选 BluRay + 填写 `directors-cut` | `bluray-directors-cut` |
| 均未勾选，填写 `hdtv-broadcast` | `hdtv-broadcast` |

## 常见来源（均未勾选 WEB / BluRay 时可用）

`dvd` · `hdtv` · `remux`

## 常见剪辑版本（区分时间轴的核心因素，可作为后缀或独立标识）

| 类型 | 常见于 | 建议标识 |
| :--- | :--- | :--- |
| 影院版 | 电影 | `theatrical` |
| 加长版 | 电影 / 纪录片 | `extended` |
| 导演剪辑版 | 电影 | `directors-cut` |
| 未分级版 | 电影 | `unrated` |
| 重制版 | 修复重发 | `remastered` |
| 周年纪念版 | 经典电影 | `anniversary` |
| 终极 / 加料版 | 系列电影 | `ultimate-edition` |
| 重剪版（Redux） | 少数电影 | `redux` |
| 电视版 | 电影 | `tv-cut` |
| 电视首播版 / 流媒体版 | 剧集 | `broadcast` / `streaming` |
| 未删减版 | 剧集 / 动画 | `uncut` |
| 剧场版 / 总集篇 | 动画剧集 | `movie-edition` / `compilation` |
| 加长访谈版 | 纪录片 | `extended-interview` |

## 区域标识

同来源、同剪辑版本，仅送审或时间轴因区域不同，可用区域码作为后缀，如 `uk`、`us`、`jp`、`cn`、`intl`。

## 标识格式要求

仅使用小写字母、数字与连字符 `-`，输入内容会自动转换（大写转小写、空格与非法字符转 `-`），无需手动处理格式。

---

<div align="center">

**蒙太奇字幕社区 (MontageSubs)**  
"用爱发电 ❤️ Powered by Love"

</div>
