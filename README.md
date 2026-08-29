# DMM-Mod

此仓库用于发布 DMM 游戏相关的**安卓版** Mod，主要提供中文翻译和部分体验改进

[DMM Mod Android](https://release.ntr.best/mod)

## 目录

- [游戏列表](#游戏列表)
- [发布相关](#发布相关)
- [功能相关](#功能相关)
- [LemonLoader 说明](#lemonloader-说明)
- [补充说明](#补充说明)
- [相关项目](#相关项目)
- [免责声明](#免责声明)

## 游戏列表

- [ドットアビス X（像素深渊）](https://dotabyssx.fanzagames-official.com/)
- [ガークリ R（少女艺术绮谭）](https://girlscreation-r.com/)
- [クルスタ X（闪耀星骑士）](https://x.twinklestarknights.jp/)
- ~~[テンパラ X（天启悖论）](https://tenkei-paradox.com/x)~~
- [STELLAR IDOL PROJECT 〜 X 〜](https://x.siprj.com/)
- [オトフロ R（童话前线）](https://games.dmm.co.jp/detail/otogi_f_r)
- [マブガル X（少女花园）](https://www.muvluv-girls-garden.com/x)

## 发布相关

发布由自动更新工作流完成。每个游戏使用独立且稳定的版本 tag：

```text
mod-<game>-v<source_version>
```

- 位置：本仓库[Releases 页面](https://github.com/anosu/DMM-Mod/releases)
- 时间：每天北京时间 14:30 和 16:30 检查更新，实际开始时间可能因 GitHub Actions 调度而延迟
- 下载：建议从 [DMM Mod Android](https://release.ntr.best/mod) 选择游戏和版本，也可以在 Releases 页面下载对应游戏的最新 APK

## 功能相关

### ドットアビス X（像素深渊）

- 主线、活动、个人剧情翻译
- 减小寝室马赛克
- 剧情角色语音不中断
- 关闭进入游戏时的音量提醒

### ガークリ R（少女艺术绮谭）

- 主线、活动、个人剧情翻译（可选）
- 文本框透明（可选，仅开启翻译时可用）

### クルスタ X（闪耀星骑士）

- 主线、活动、个人剧情翻译

游戏进去有 6g 的数据要下载，安装新的 apk 之前可以先从已经安装的 app 数据目录中备份缓存，新的 apk 安装好之后直接把缓存复制过去，就不用重下 6 的数据

缓存位置: `/storage/emulated/0/Android/data/包名/files/UnityCache`

### ~~テンパラ X（天启悖论）~~

- 主线、部分活动剧情翻译（其他的剧情需要供档，暂未补充）
- 去除游戏内动态加载的马赛克（不包含 Spine 源文件上的码）

### STELLAR IDOL PROJECT 〜 X 〜

- **该 Mod 为个人自用，不保证任何安全和稳定性**
- 减小马赛克
- 剧情翻译（实验性）
- 开启战斗的跳过按钮，允许后台战斗
- 剧情播放语音不中断，文本框透明
- 跳过剧情不需要确认

### オトフロ R（童话前线）

- 角色剧情翻译，来自[otogitranslate](https://github.com/alex343425/otogitranslate)
- 固定帧率为 60
- 移除游戏内动态添加的马赛克（虽然这对实际体验影响可能不大）

### マブガル X（少女花园）

- 剧情翻译（实验性）
- 减小马赛克
- 总是开启剧情跳过按钮
- 自动跳过战斗（可选）
- 剧情语音不中断（可选）

## LemonLoader 说明

像素深渊和少女花园使用 LemonLoader 加载 C# Mod，首次成功进入游戏后会自动创建运行目录、配置文件和日志文件

### 数据目录

LemonLoader 的根目录位于修改版应用自己的外部数据目录中，其中 `<包名>` 是安装后实际使用的 `.mod` 包名

```text
/storage/emulated/0/Android/data/<包名>/files/MelonLoader
```

Android 11 及更高版本通常会限制普通文件管理器访问 `Android/data`，可使用支持该目录授权的文件管理器或 ADB 访问

| 内容     | 相对 LemonLoader 根目录的位置 |
| -------- | ----------------------------- |
| 当前日志 | `MelonLoader/Latest.log`      |
| 历史日志 | `MelonLoader/Logs/`           |
| Mod 文件 | `Mods/`                       |
| Mod 配置 | `UserData/`                   |
| 翻译缓存 | `UserData/<Mod名称>/`         |

### Mod 配置文件

配置文件会在 Mod 首次成功加载时自动生成，修改前应完全退出游戏，修改后重新启动游戏

| 游戏     | 配置文件                 |
| -------- | ------------------------ |
| 像素深渊 | `UserData/AbyssMod.cfg`  |
| 少女花园 | `UserData/MuvluvMod.cfg` |

像素深渊常用配置如下

| 分类与配置项                | 默认值  | 用途                               |
| --------------------------- | ------- | ---------------------------------- |
| `General.DynamicMosaic`     | `false` | 是否启用游戏内动态马赛克           |
| `General.SoundCaution`      | `false` | 是否显示进入游戏时的音量提醒       |
| `General.VoiceInterruption` | `false` | 下一段无声文本是否中断当前角色语音 |
| `General.TitleMovie`        | `true`  | 是否播放进入游戏时的标题动画       |
| `General.NovelLive2DScale`  | `1.0`   | 剧情 Live2D 缩放倍率               |
| `Translation.Enabled`       | `true`  | 是否启用翻译                       |

少女花园常用配置如下

| 分类与配置项                | 默认值  | 用途                           |
| --------------------------- | ------- | ------------------------------ |
| `General.DynamicMosaic`     | `false` | 是否启用游戏内动态马赛克       |
| `General.EnableSkipButton`  | `true`  | 是否总是开启跳过按钮           |
| `General.VoiceInterruption` | `false` | 播放下一句话时是否中断当前语音 |
| `General.AutoSkipBattle`    | `false` | 是否自动触发战斗跳过           |
| `Translation.Enable`        | `true`  | 是否启用翻译                   |

翻译开关、CDN、语言、缓存目录和字体路径等启动期配置修改后需要重启游戏才能完整生效

### 字体与缓存

安装包已经包含对应字体，默认位置如下

| 游戏     | 字体文件                                 | 默认翻译缓存                      |
| -------- | ---------------------------------------- | --------------------------------- |
| 像素深渊 | `UserData/AbyssMod/ttcuyuanj`            | `UserData/AbyssMod/translations/` |
| 少女花园 | `UserData/MuvluvMod/sarasagothicsc-bold` | `UserData/MuvluvMod/translation/` |

通常不需要修改字体路径，字体加载失败时可先检查文件是否存在，再查看 `Latest.log` 中的错误信息

### 更新与排障

- 使用相同 `.mod` 包名和签名直接覆盖安装时，配置、翻译缓存和游戏数据通常会保留
- 卸载应用会删除对应应用数据，更新前不要先卸载，需要时先备份整个应用数据目录
- 配置文件没有生成时，先检查 `Latest.log` 中是否出现 LemonLoader 启动、Mod 加载和配置初始化记录
- Mod 功能异常时优先提供本次启动生成的 `Latest.log`，历史问题可同时查看 `Logs/`
- 不要在游戏运行期间替换 DLL、字体或配置文件，以免读取到未写完的内容

## 补充说明

- 如果功能不生效，请重启手机系统后再尝试；仍然无效时，可能是当前设备或游戏版本不兼容
- 如果出现闪退，请尝试更换版本，如果仍然闪退，那就是用不了
- 安装包默认修改包名，与官方安装包不冲突
- 当前仅支持 64 位 ARM 设备（arm64-v8a）
- 像素深渊和少女花园使用 LemonLoader 加载 C# Mod，其他游戏目前主要使用 Frida Gadget
- 像素深渊
    - 只提供一个版本，如果用不了那就是用不了
- 闪耀星骑士
    - 星骑士 Mod 的原始 C#实现和翻译均来自[TSKHook](https://github.com/TSKModding/TSKHook)
    - 原作者维护了一个工作流，功能相同，未修改包名，没有共存需求建议用这个[TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)
- 少女艺术绮谭
    - 翻译使用 DeepSeek V4 Flash 模型
- 天启悖论
    - 原项目（翻译以及 BepInEx 插件）地址：https://github.com/anosu/tenkeiparadoxx-translation
- 童话前线
    - 翻译来源以及网页版插件：[alex343425/otogitranslate](https://github.com/alex343425/otogitranslate)

## 相关项目

- [AbyssMod](https://github.com/anosu/AbyssMod)
- [AbyssMod-Android](https://github.com/anosu/AbyssMod-Android)
- [MuvluvMod-Android](https://github.com/anosu/MuvluvMod-Android)
- [LemonLoader](https://github.com/anosu/LemonLoader)
- [TSKHook](https://github.com/TSKModding/TSKHook)
- [TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)
- [GCMod](https://github.com/anosu/GCMod)
- [tenkeiparadoxx-translation](https://github.com/anosu/tenkeiparadoxx-translation)

## 免责声明

本仓库内容仅供学习交流使用，请遵守游戏版权法律法规，请勿用于任何商业用途

不保证绝对稳定，可能会出现对话文本错乱，字体缺失，游戏闪退等现象

**理论上不会封号，但是任何 Mod 均有风险，用别怕，怕别用**

如有侵权，请发送邮件至jitsu233@gmail.com
