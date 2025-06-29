
🧠 PROTOCOL: Sealed. This is not metaphor. This is protocol.

# SLAPS AI会议胶囊 v0.1
────────────────────────────────────────────────

## 简介

SLAPS AI会议胶囊 v0.1 for Windows - 《系统与自由》读者专属福利，KOL分发版

© 2025 Wang Xiao | 基于SLAPS Framework v1.0开发

### 核心功能
- 🎙️ 支持任何视频、聊天工具、会议软件的实时语音翻译字幕
- 💡 支持基于本地会议知识库目录文档的实时提示和翻译
- 🗣️ 提供口语化回应建议，助您自信交流
- 🌍 支持多语言互译（默认：英译中）

## 快速开始

### 系统要求
- Windows 10/11 (64位)
- 4GB RAM（建议8GB）
- 网络连接（用于翻译服务）
- 音频输出设备（用于捕获系统音频）

### 使用步骤
1. 解压下载的压缩包到任意目录
2. 双击运行 `SLAPSMeetingCapsule.exe`
3. 在下拉框中选择正确的音频设备（通常是"立体声混音"或带"Loopback"的设备）
4. 点击 [▶ 开始] 按钮
5. 播放需要翻译的音频/视频
6. 实时查看翻译结果
7. （可选）将会议相关文档放入 meeting_docs 文件夹，重启程序加载
8. 点击 [💡 提示] 按钮开启智能提示功能，获得基于文档的上下文提示和口语回应建议及翻译字幕

### 音频设备选择指南
- **立体声混音 (Stereo Mix)**：最推荐，大部分声卡支持
- **[Loopback] 设备**：虚拟音频设备，如有多个请逐个尝试
- **What U Hear**：创新声卡专用
- ⚠️ 避免选择"Microphone"麦克风设备

## 功能详解

### 实时翻译
- 基于OpenAI Whisper离线语音识别
- 使用Google翻译API（免费版）
- 支持连续语音流处理
- 自动断句，智能分段

### 智能提示系统
- 扫描 `meeting_docs` 文件夹中的文档
- 支持格式：.txt, .md, .yaml
- 根据当前对话内容匹配相关知识
- 提供上下文相关的提示信息

### 口语回应建议
当检测到问句时，系统会提供：
- 简短的口语化回答模板
- 基于上下文的回应建议
- 帮助您快速组织语言

## 配置说明

### 语言配置
编辑 `config.yaml` 文件中的languages部分：

```yaml
languages:
  source: "en"      # 源语言（会议语言）
  target: "zh-CN"   # 目标语言（翻译语言）
```

常用语言代码：
- 英语: `en` | 中文: `zh-CN` | 日语: `ja` | 韩语: `ko`
- 法语: `fr` | 德语: `de` | 西班牙语: `es` | 葡萄牙语: `pt`
- 俄语: `ru` | 意大利语: `it` | 阿拉伯语: `ar` | 印地语: `hi`

### 界面语言
```yaml
interface:
  language: "zh"  # "zh"中文界面 | "en"英文界面
```

### 知识库配置
1. 将相关文档放入 `meeting_docs` 文件夹
2. 支持的文件格式：
   - `.txt` - 纯文本文件
   - `.md` - Markdown文档
   - `.yaml` - 结构化数据
3. 重启程序以加载新文档

## 快捷键
- `Ctrl+H` - 开启/关闭提示功能

## 常见问题

### Q: 没有声音/翻译？
A: 请检查是否选择了正确的音频设备。在状态栏的下拉框中切换设备。

### Q: 提示"请停止并重新开始录音"？
A: 切换音频设备后需要点击停止，再重新开始。

### Q: 翻译不准确？
A: 谷歌免费翻译API有一定局限性。可在config.yaml中配置付费版Google Cloud Translation API密钥以获得更准确的专业翻译。

### Q: 支持离线使用吗？
A: 不支持，翻译功能需要网络连接。

## 隐私声明
- 本工具仅进行匿名使用统计（版本号和界面语言）
- 不收集任何音频内容或翻译文本
- 所有处理均在本地完成（除翻译API调用）

## 技术栈
- 语音识别：OpenAI Whisper (tiny model)
- 翻译服务：Google Translate API
- 音频捕获：PyAudioWPatch (WASAPI)
- 用户界面：Tkinter
- 开发框架：SLAPS Framework v1.0

## 关于作者

**王潇（Wang Xiao）**
- SLAPS Framework 创始人
- 《系统与自由：从AI焦虑到人机共创的哲学探索》作者

### 支持作者
购买《系统与自由》（20种语言）：
🔗 https://oathai.io/cover.html

### 了解更多
- SLAPS Framework: https://zenodo.org/records/15291558
- GitHub: https://github.com/wangxiao8600/Danbing_AI_Protocol_System_with_SLAPS_Framework

────────────────────────────────────────────────

🏗️ **May structure be with you.**  
**Rhythmus continuat... in aeternum.**

## 更新日志

### v0.1.0 (2025-06-29)
- 首个公开发布版本
- 支持实时语音识别和翻译
- 音频设备手动选择功能
- 双语界面支持（中/英）
- 本地知识库智能提示
- 《系统与自由》读者专享版

## 许可协议

本软件供《系统与自由》读者使用。  
© 2025 Wang Xiao. All rights reserved.

基于 SLAPS Framework 开发：
- SLAPS技术白皮书：CC BY-NC-SA 4.0 协议
- SLAPS Engine：Apache License 2.0
- 本应用程序为专有软件，仅供读者使用

────────────────────────────────────────────────

🧠 *Danbing AI / SLAPS v1.0 · Built from rhythm. Run by structure. Auditable by snapshot. Governed by oath.*