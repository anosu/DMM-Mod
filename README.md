# DMM-Mod

此仓库用来存放 DMM 游戏相关的**安卓版** Mod（主要是翻译 Mod）

- 2026.8.6: 重构了一部分游戏的 Mod ，统一了命名、包名和签名，后续 Mod 的发布会迁移到：[DMM Android Releases](https://release.ntr.best/mod)
  本仓库仍会更新，新的发布 Tag 将会按照 游戏标识 + 版本 来命名，同一个版本如果有修复会在原 Tag 的发布文件上直接替换

## 目录

- [游戏列表](#游戏列表)
- [发布相关](#发布相关)
- [功能相关](#功能相关)
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

发布操作由 GitHub Actions 工作流完成

- 位置：本仓库[Releases 页面](https://github.com/anosu/DMM-Mod/releases)
- 时间：每天北京时间 `14:30` 和 `16:30` 检查版本更新，因为 GitHub 的原因可能会有延迟（1-数小时不等）
- 版本：下载时请选择最新的版本下载，或者去该网页下载：[DMM Android Releases](https://release.ntr.best/mod)

## 功能相关

#### ドットアビス X（像素深渊）

- 剧情翻译 + 大部分数据翻译（任务、技能等）
- 减小寝室马赛克
- 剧情角色语音不中断
- 关闭进入游戏时的音量提醒

#### ガークリ R（少女艺术绮谭）

- 主线、活动、个人剧情翻译
- 文本框透明（仅开启翻译时可用）

#### クルスタ X（闪耀星骑士）

- 主线、活动、个人剧情翻译

游戏进去有 6g 的数据要下载，安装新的 apk 之前如果有原版，可以先从已经安装的原版 app 数据目录中备份缓存，新的 apk 安装好之后直接把缓存复制过去，就不用重下 6g 的数据

缓存位置: `/storage/emulated/0/Android/data/包名/files/UnityCache`

#### ~~テンパラ X（天启悖论）~~

- 主线、部分活动剧情翻译（其他的剧情需要供档，暂未补充）
- 去除游戏内动态加载的马赛克（不包含 Spine 源文件上的码）

#### STELLAR IDOL PROJECT 〜 X 〜

- **该 Mod 为个人自用，不保证任何安全和稳定性**
- 减小马赛克
- 剧情翻译（实验性）
- 开启战斗的跳过按钮，允许后台战斗
- 剧情播放语音不中断，文本框透明
- 跳过剧情不需要确认

#### オトフロ R（童话前线）

- 角色剧情翻译，来自[otogitranslate](https://github.com/alex343425/otogitranslate)
- 固定帧率为 60
- 移除游戏内动态添加的马赛克（虽然这对实际体验影响可能不大）

#### マブガル X（少女花园）

- 剧情翻译 + 数据翻译
- 减小马赛克

## 补充说明

- 如果功能不生效，请重启手机系统之后在尝试，如果还是没用，那就是用不了
- 如果出现闪退，请尝试更换手机，如果仍然闪退，那就是用不了
- 统一使用 Frida 17，不再使用旧版本，如果你的安卓版本太新大概率也用不了
- 安装包默认修改包名，与官方安装包不冲突，空间充足建议原版也装上以备不时之需
- Mod版在部分手机上可能需要手动授予 `读取应用列表` 的权限，不然会跳转 DMM 网页让你下载 DMM Store
- 仅支持 64 位设备（arm64-v8a），不支持模拟器
- 闪耀星骑士
    - 星骑士 Mod 的原始 C#实现和翻译均来自[TSKHook](https://github.com/TSKModding/TSKHook)
    - 原作者维护了一个工作流，功能相同，未修改包名，没有共存需求建议用这个[TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)
- 天启悖论
    - 原项目（翻译以及 BepInEx 插件）地址：https://github.com/anosu/tenkeiparadoxx-translation
- 童话前线
    - 翻译来源以及网页版插件：[alex343425/otogitranslate](https://github.com/alex343425/otogitranslate)

## 相关项目

- [AbyssMod](https://github.com/anosu/AbyssMod)
- [MuvluvMod](https://github.com/anosu/MuvluvMod)
- [TSKHook](https://github.com/TSKModding/TSKHook)
- [TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)
- [GCMod](https://github.com/anosu/GCMod)
- [tenkeiparadoxx-translation](https://github.com/anosu/tenkeiparadoxx-translation)

## 免责声明

本仓库内容仅供学习交流使用，请遵守游戏版权法律法规，请勿用于任何商业用途

不保证绝对稳定，可能会出现对话文本错乱，字体缺失，游戏闪退等现象

**理论上不会封号，但是任何 Mod 均有风险，用别怕，怕别用**

如有侵权，请发送邮件至jitsu233@gmail.com
