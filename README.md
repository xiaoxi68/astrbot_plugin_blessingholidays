# 🤖 AstrBot 节日祝福插件 (BlessingHolidays)

## 修改自cheng-maomao的SendBlessings插件

---

## 📖 简介

**blessingholidays** 是一款为 [AstrBot](https://github.com/AstrBotDevs/AstrBot) 设计的自动化节日祝福插件。它能够自动检测中国的法定节假日，并在假期的第一天向所有好友和群组广播节日祝福（纯文本）。同时，它还会在假期的最后一天晚上发送温馨的“收假”提醒。

插件可选使用 LLM（大型语言模型）生成个性化祝福语

## ✨ 功能特点

-   **自动检测节假日**: 自动获取并缓存当前年份的法定节假日信息，无需手动干预。
-   **双重祝福模式**:
    -   **假期开始**: 在每个法定节假日的指定时间（默认 00:05，可配置）向所有好友和群组广播祝福。
    -   **假期结束**: 在假期最后一天的指定时间（默认为22:00）发送温馨的“收假”提醒。
-   （当前未启用）图片生成：功能已禁用。
-   **智能祝福语**: 可选地使用已配置的LLM为两种祝福场景生成更具人情味的个性化祝福语。
-   **广播模式**: 所有祝福均自动发送给机器人所在的所有群组和所有好友，无需繁琐配置。
-   **管理员工具**: 提供丰富的管理员命令，方便进行测试、重载数据和手动发送祝福。

## ⚙️ 安装与配置

1. **下载插件**: 推荐使用AstrBot的插件管理器安装。或者将插件文件夹放置于 AstrBot 的 `data/plugins` 目录下，并手动安装依赖。
2. **配置插件**: 在 AstrBot 的 WebUI 中，进入“插件管理”，找到“blessingholidays”插件，点击“配置”按钮进行可视化配置。

### 🔧 配置项说明

> 注：当前为纯文本模式，图片与参考图相关配置项暂不生效。

-   `enabled`: 是否启用插件 (布尔型, 默认: `true`)。
-   `llm_provider_id`: 选择用于生成祝福的 LLM 提供商（从 AstrBot WebUI 已配置提供商中选择）。
-   `holidays_file`: 节假日数据缓存文件名 (字符串, 默认: `holidays.json`)。
-   `test_targets`: 测试命令的目标配置 (对象，可选)。
    -   `group_ids`: 群组 ID 列表 (列表)。
    -   `user_ids`: 用户 ID 列表 (列表)。
-   `start_of_holiday_blessing`: 假期首日祝福配置 (对象)。
    -   `send_time`: 每日发送时间 (字符串, 格式为 "HH:MM", 默认: `"00:05"`)。
-   `end_of_holiday_blessing`: 假期结束提醒配置 (对象)。
    -   `enabled`: 是否启用假期结束提醒功能 (布尔型, 默认: `true`)。
    -   `send_time`: 每日发送时间 (字符串, 格式为 "HH:MM", 默认: `"22:00"`)。

## 🚀 使用方法

插件的核心功能是全自动的，配置完成后即可在节假日自动发送祝福。此外，插件还提供了一些方便管理的命令。

### 👨‍💻 管理员命令

-   `/blessings reload`: 重新从网络获取并加载当前年份的节假日数据。
-   `/blessings check`: 检查今天是否是节假日的第一天，并返回检查结果。
-   `/blessings manual [holiday_name]`: 手动触发一次祝福生成和发送流程。如果提供了 `holiday_name`，则使用该名称。该命令会将祝福发送到**当前会话**，主要用于测试。
*暂时无法实现*-   ~~`/blessings test [holiday_name]`: 手动向所有好友和群组广播一次测试祝福。


## 🛠️ 技术实现

-   **节假日数据**: 使用 `chinese-calendar` 库获取中国的法定节假日和调休信息。
-   **祝福语生成**: 优先尝试使用 AstrBot 中配置的LLM提供商生成祝福语，如果失败则回退到内置的模板祝福语。

## 🗺️ 未来规划
- [ ] 支持更多节日（如西方节日）

## 📦 使用的第三方库
- [AstrBot](https://github.com/AstrBotDevs/AstrBot) 提供的强大、灵活的机器人平台
- [cn_bing_translator](https://github.com/minibear2021/cn_bing_translator) 提供的翻译功能
- [chinese-calendar](https://github.com/LKI/chinese-calendar) 提供的中国节假日获取功能

## 📄 许可证
本项目采用 AGPL-3.0 许可证，详情请参阅 [LICENSE](https://github.com/xiaoxi68/astrbot_plugin_blessingholidays?tab=AGPL-3.0-1-ov-file#readme) 文件。
