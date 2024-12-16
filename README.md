# DMM-Mod

此仓库用来存放DMM游戏相关的**安卓版**Mod（主要是翻译Mod）

## 目录

- [游戏列表](#游戏列表)
- [发布相关](#发布相关)
- [功能相关](#功能相关)
- [补充说明](#补充说明)
- [相关项目](#相关项目)
- [免责声明](#免责声明)


## 游戏列表

- [ガークリR（少女艺术绮谭）](https://girlscreation-r.com/)
- [クルスタX（闪耀星骑士）](https://x.twinklestarknights.jp/)


## 发布相关

发布操作由GitHub Actions工作流完成，tag名为操作执行的时间（UTC+0时间）

- 位置：本仓库[Releases页面](https://github.com/anosu/DMM-Mod/releases)
- 时间：每天北京时间下午4点检查版本更新
- 版本：下载时请选择最新tag的最新版下载


## 功能相关

#### ガークリR（少女艺术绮谭）

- 主线、活动、个人剧情翻译（可选）
- 文本框透明（可选，仅开启翻译时可用）

#### クルスタX（闪耀星骑士）

- 主线、活动、个人剧情翻译

游戏进去有4g的数据要下载，安装新的apk之前可以先从已经安装的app数据目录中备份缓存，新的apk安装好之后直接把缓存复制过去，就不用重下4g的数据

缓存位置: `/storage/emulated/0/Android/data/包名/files/UnityCache`


## 补充说明

- 安装包默认修改包名，与官方安装包不冲突
- 采用Frida实现修改，仅支持64位设备（arm64-v8a）
- 闪耀星骑士
    - 星骑士Mod的原始C#实现和翻译均来自[TSKHook](https://github.com/TSKModding/TSKHook)
    - 原作者维护了一个工作流，功能相同，未修改包名，没有共存需求建议用这个[TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)
- 少女艺术绮谭
    - 翻译使用SakuraLLM v0.9-14b模型


## 相关项目

- [TSKHook](https://github.com/TSKModding/TSKHook)
- [TSKHook-frida](https://github.com/TSKModding/TSKHook-frida)
- [GCMod](https://github.com/anosu/GCMod)


## 免责声明

本仓库内容仅供学习交流使用，请遵守游戏版权法律法规，请勿用于任何商业用途

不保证绝对稳定，可能会出现对话文本错乱，字体缺失，游戏闪退等现象

**理论上不会封号，但是任何Mod均有风险，用别怕，怕别用**

如有侵权，请发送邮件至jitsu233@gmail.com