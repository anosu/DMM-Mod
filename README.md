# DMM-Mod

DMM 游戏安卓版 Mod 发布仓库，主要提供中文翻译、显示调整和部分操作体验改进

> [!WARNING]
> 使用前请完整阅读安装、更新和风险说明，Mod 可能因游戏更新、设备环境或系统限制失效

- 下载入口：[DMM Mod Android](https://release.ntr.best/mod)
- GitHub 发布页：[Releases](https://github.com/anosu/DMM-Mod/releases)
- 支持架构：Android ARM64 `arm64-v8a`

## 目录

- [快速开始](#快速开始)
- [支持的游戏](#支持的游戏)
- [下载与发布](#下载与发布)
- [安装与更新](#安装与更新)
- [LemonLoader](#lemonloader)
- [游戏说明](#游戏说明)
    - [像素深渊](#dotabyss)
    - [少女艺术绮谭](#girlscreation)
    - [闪耀星骑士](#twinklestarknights)
    - [天启悖论](#tenkeiparadox)
    - [STELLAR IDOL PROJECT](#siprj)
    - [童话前线](#otogifrontier)
    - [少女花园](#muvluvgg)
- [常见问题](#常见问题)
- [免责声明](#免责声明)

## 快速开始

1. 确认设备为 64 位 ARM Android 设备（除非你是特别老的设备，否则一般不用管）
2. 从 [DMM Mod Android](https://release.ntr.best/mod) 选择游戏并下载最新 APK
3. 按系统提示允许当前浏览器或文件管理器安装未知来源应用
4. 安装后直接启动修改版应用，部分系统可能需要手动授予 `允许读取应用列表` 的权限用于检测DMM Store，否则会跳转浏览器要求下载
5. 使用 LemonLoader 的游戏首次启动后，Mod 会在 "Android/data" 对应的目录下自动生成配置和日志

修改版 APK 会在官方包名后追加 `.mod`，因此通常可以与官方应用同时安装，但两者的游戏数据、资源缓存和设置互不共享

## 支持的游戏

| 游戏                                                         | 中文名               | 状态       | Mod 运行方式 |
| ------------------------------------------------------------ | -------------------- | ---------- | ------------ |
| [ドットアビス X](https://dotabyssx.fanzagames-official.com/) | 像素深渊             | 维护中     | LemonLoader  |
| [ガークリ R](https://girlscreation-r.com/)                   | 少女艺术绮谭         | 维护中     | Frida Gadget |
| [クルスタ X](https://x.twinklestarknights.jp/)               | 闪耀星骑士           | 维护中     | LemonLoader  |
| [テンパラ X](https://tenkei-paradox.com/x)                   | 天启悖论             | 已停止维护 | Frida Gadget |
| [STELLAR IDOL PROJECT 〜 X 〜](https://x.siprj.com/)         | STELLAR IDOL PROJECT | 实验性     | Frida Gadget |
| [オトフロ R](https://games.dmm.co.jp/detail/otogi_f_r)       | 童话前线             | 维护中     | Frida Gadget |
| [マブガル X](https://www.muvluv-girls-garden.com/x)          | 少女花园             | 维护中     | LemonLoader  |

## 下载与发布

APK 由自动工作流构建和发布，每个游戏使用独立 tag

```text
mod-<game>-v<source_version>
```

`source_version` 通常取自 DMM Store 返回的应用版本代码，与游戏内显示的版本号不同

- 每天北京时间 14:15 和 16:15 检查更新
- GitHub Actions 可能因排队而延迟开始
- 聚合站适合直接查找当前版本，Releases 页面适合查看历史版本和发布记录
- 游戏 APK、Mod 部署包或构建配方发生变化时，工作流会按对应目标重新构建

## 安装与更新

### 首次安装

修改版与官方版使用不同包名，安装后会显示为独立应用，官方版的数据不会自动复制到修改版

### 覆盖更新

使用本站发布的同一游戏新版 APK 直接覆盖安装即可，正常情况下会保留游戏数据、LemonLoader 配置和翻译缓存

不要为了更新先卸载旧版，卸载会同时删除该 `.mod` 包名下的全部应用数据

如果系统拒绝覆盖安装，通常是签名、包名或版本降级导致，此时先备份数据再决定是否卸载重装

### 应用数据

修改版应用的数据通常位于以下目录，其中 `<包名>` 是安装后实际使用的 `.mod` 包名

```text
/storage/emulated/0/Android/data/<包名>/
```

Android 11 及更高版本通常会限制普通文件管理器访问 `Android/data`，可使用支持目录授权的文件管理器或 ADB 操作

## LemonLoader

部分游戏使用使用 LemonLoader 加载 C# Mod，包括：

- 像素深渊
- 闪耀星骑士
- 少女花园

项目地址：[anosu/LemonLoader](https://github.com/anosu/LemonLoader)

> [!WARNING]
> 不保证兼容性，部分设备可能会出现闪退或者功能无效等问题，届时可以在本仓库中提 issue，并确保附上相关日志文件以便排查，设备信息等，如果你是专业人士建议附上崩溃部分 logcat 日志

### 运行目录

LemonLoader 根目录位于修改版应用的外部数据目录

```text
/storage/emulated/0/Android/data/<包名>/files/MelonLoader
```

以下路径均相对于上述 `MelonLoader` 根目录

| 内容           | 路径         |
| -------------- | ------------ |
| 当前启动日志   | `Latest.log` |
| 历史日志       | `Logs/`      |
| Mod 文件       | `Mods/`      |
| Mod 配置和数据 | `UserData/`  |

### 配置规则

- 配置文件会在对应 Mod 首次成功加载时生成
- 编辑配置前应完全退出游戏
- 布尔值使用 `true` 或 `false`
- 配置项名称和分类必须保持不变
- 启动期配置修改后需要重新启动游戏
- 不要在游戏运行期间替换 DLL、字体或配置文件

配置文件没有生成或功能异常时，先检查 `Latest.log` 中是否出现 LemonLoader 启动、Mod 加载和配置初始化记录

## 游戏说明

<a id="dotabyss"></a>

### ドットアビス X（像素深渊）

#### 功能

- 剧情翻译和部分数据文本翻译
- 减小寝室马赛克
- 剧情角色语音不中断
- 可关闭进入游戏时的音量提醒
- 可关闭进入游戏时的标题动画
- 可调整剧情 Live2D 缩放倍率

#### 配置

配置文件：`UserData/AbyssMod.cfg`

| 配置项                      | 默认值  | 用途                               |
| --------------------------- | ------- | ---------------------------------- |
| `General.DynamicMosaic`     | `false` | 是否启用游戏内动态马赛克           |
| `General.SoundCaution`      | `false` | 是否显示进入游戏时的音量提醒       |
| `General.VoiceInterruption` | `false` | 下一段无声文本是否中断当前角色语音 |
| `General.TitleMovie`        | `true`  | 是否播放进入游戏时的标题动画       |
| `General.NovelLive2DScale`  | `1.0`   | 剧情 Live2D 缩放倍率               |
| `Translation.Enabled`       | `true`  | 是否启用翻译                       |

翻译开关、CDN、语言、缓存目录和字体路径属于启动期配置，修改后需要重启游戏

#### 数据文件

| 内容     | 路径                              |
| -------- | --------------------------------- |
| 字体     | `UserData/AbyssMod/ttcuyuanj`     |
| 翻译缓存 | `UserData/AbyssMod/translations/` |

#### 相关项目

- [AbyssMod](https://github.com/anosu/AbyssMod)
- [AbyssMod-Android](https://github.com/anosu/AbyssMod-Android)

<a id="girlscreation"></a>

### ガークリ R（少女艺术绮谭）

#### 功能

- 主线、活动、个人剧情和主页角色语音文本翻译
- 文本框透明，可在启用翻译时选择开启

#### 注意事项

翻译使用 DeepSeek V4 Flash 模型生成，可能存在错译或上下文不一致

#### 相关项目

- [GCMod](https://github.com/anosu/GCMod)

<a id="twinklestarknights"></a>

### クルスタ X（闪耀星骑士）

#### 功能

- 固定游戏速度倍率，并在游戏重置后自动恢复
- 设置并保持目标帧率
- 角色名、剧情标题和剧情文本繁体中文翻译
- 翻译下载、本地缓存和网络失败回退
- Utage 与 TextMeshPro 中文字体替换
- 图鉴角色缩放倍率调整
- Mod 加载、配置变更、翻译和字体状态 Toast 提示

#### 配置

配置文件：`UserData/TSKHook.cfg`

| 配置项                               | 默认值                                         | 用途                                      |
| ------------------------------------ | ---------------------------------------------- | ----------------------------------------- |
| `General.GameSpeed`                  | `1.0`                                          | 游戏速度倍率，允许范围为 `0.1` 到 `10`    |
| `General.TargetFrameRate`            | `60`                                           | 目标帧率，允许范围为 `30` 到 `240`        |
| `General.ZoomRatio`                  | `1.0`                                          | 图鉴角色缩放倍率，允许范围为 `0.1` 到 `5` |
| `Translation.Enable`                 | `true`                                         | 是否启用繁体中文翻译                      |
| `Translation.CDN`                    | `https://translation.lolida.best/download/tsk` | 翻译内容下载地址                          |
| `Translation.Language`               | `zh_Hant`                                      | 翻译语言，目前支持繁体中文                |
| `Translation.Cache.Directory`        | `TSKHook/translations`                         | 相对于 `UserData` 的翻译缓存目录          |
| `Translation.Cache.PreferLocalFiles` | `false`                                        | 是否优先使用本地翻译并跳过下载            |

游戏速度、目标帧率和缩放倍率修改后会自动生效，翻译、缓存和字体配置需要重启游戏

#### 数据文件

| 内容         | 路径                                                       |
| ------------ | ---------------------------------------------------------- |
| 字体         | `UserData/TSKHook/notosanscjktc`                           |
| 翻译缓存     | `UserData/TSKHook/translations/`                           |
| 游戏资源缓存 | `/storage/emulated/0/Android/data/<包名>/files/UnityCache` |

#### 注意事项

首次进入大约需要下载 6 GB 游戏资源，正常覆盖更新不需要手动搬运缓存

必须卸载重装或更换包名时，可提前备份 `UnityCache`，重新安装并启动一次游戏后完全退出，再把备份内容复制到新应用的相同位置

原作者还维护了 [TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)，该版本使用官方包名，不适合与官方版共存，但没有共存需求时也可直接使用

#### 相关项目

- [TSKHook](https://github.com/TSKModding/TSKHook)
- [TSKHook-Android](https://github.com/anosu/TSKHook-Android)

<a id="tenkeiparadox"></a>

### ~~テンパラ X（天启悖论）~~

#### 功能

- 主线和部分活动剧情翻译
- 去除游戏内动态加载的马赛克，不包含 Spine 源文件上的马赛克

#### 注意事项

游戏已停止服务

#### 相关项目

- [tenkeiparadoxx-translation](https://github.com/anosu/tenkeiparadoxx-translation)

<a id="siprj"></a>

### STELLAR IDOL PROJECT 〜 X 〜

> [!CAUTION]
> 此 Mod 原为个人自用，功能处于实验状态，不保证安全性和稳定性

#### 功能

- 减小马赛克
- 实验性剧情翻译
- 开启战斗跳过按钮并允许后台战斗
- 剧情语音不中断和文本框透明
- 跳过剧情时不再要求确认

<a id="otogifrontier"></a>

### オトフロ R（童话前线）

#### 功能

- 角色剧情翻译
- 固定帧率为 60
- 移除游戏内动态添加的马赛克

#### 相关项目

- [otogitranslate](https://github.com/alex343425/otogitranslate)：角色剧情翻译和网页版插件

<a id="muvluvgg"></a>

### マブガル X（少女花园）

#### 功能

- 剧情翻译和部分数据文本翻译
- 减小马赛克
- 总是开启战斗跳过按钮
- 可选自动跳过战斗
- 可选剧情语音不中断

#### 配置

配置文件：`UserData/MuvluvMod.cfg`

| 配置项                      | 默认值  | 用途                           |
| --------------------------- | ------- | ------------------------------ |
| `General.DynamicMosaic`     | `false` | 是否启用游戏内动态马赛克       |
| `General.EnableSkipButton`  | `true`  | 是否总是开启战斗跳过按钮       |
| `General.VoiceInterruption` | `false` | 播放下一句话时是否中断当前语音 |
| `General.AutoSkipBattle`    | `false` | 是否自动触发战斗跳过           |
| `Translation.Enable`        | `true`  | 是否启用翻译                   |

翻译开关、CDN、语言、缓存目录和字体路径属于启动期配置，修改后需要重启游戏

#### 数据文件

| 内容     | 路径                                     |
| -------- | ---------------------------------------- |
| 字体     | `UserData/MuvluvMod/sarasagothicsc-bold` |
| 翻译缓存 | `UserData/MuvluvMod/translation/`        |

#### 相关项目

- [MuvluvMod-Android](https://github.com/anosu/MuvluvMod-Android)

## 常见问题

### Mod 功能没有生效

先完全退出游戏并重新启动，仍然无效时重启手机，再确认当前 APK 与游戏版本是否匹配

LemonLoader 游戏应检查 `Latest.log` 中是否出现对应 Mod 的加载记录

### 配置文件没有生成

配置文件只会在 Mod 成功加载后生成，先查看 `Latest.log`，确认对应 DLL 已从 `Mods/` 目录加载

### 游戏启动后闪退

先确认设备为 ARM64，并尝试安装最新发布版本

持续闪退通常表示当前设备、系统环境或游戏版本不兼容，可在反馈时附上游戏版本、设备型号、Android 版本和日志

### 翻译或字体异常

检查网络、字体文件和翻译缓存目录，必要时备份后删除对应游戏的翻译缓存，让 Mod 重新下载

字体加载失败时先确认对应游戏部分列出的字体文件存在，再检查 `Latest.log` 中的加载错误

### 无法访问 `Android/data`

这是 Android 11 之后的系统限制，并非 Mod 创建目录失败，可改用支持存储访问框架授权的文件管理器或通过 ADB 访问

## 免责声明

本仓库内容仅供学习和交流，请遵守相关法律法规及游戏服务条款，不得用于商业用途

Mod 可能造成闪退、文本错乱、字体缺失、账号处罚或数据损坏，使用者需自行判断并承担风险

本项目不承诺持续更新，也不保证兼容所有设备、系统版本和游戏版本

如有侵权或其他问题，请发送邮件至 `jitsu233@gmail.com`
