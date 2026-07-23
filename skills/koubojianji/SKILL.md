---
name: koubojianji
description: "Plan and edit Chinese talking-head videos for Douyin/TikTok through a mandatory approval-gated workflow: first inspect the script, talking-head recording, related videos, images, and screen recordings; then produce a timestamped shot-by-shot editing plan; only after explicit user confirmation, create the polished vertical video with content-aware cuts, Chinese-English bilingual captions, tech information cards, circular speaker picture-in-picture, XingXingDaRen branding, validation, and final export. Use whenever the user says “帮我剪辑一下这个口播视频”, “剪一下口播”, “先出剪辑方案”, “做口播视频”, “加中英双语字幕”, “剪AI工具教程”, or provides talking-head materials and asks Codex to plan, edit, package, subtitle, or export them."
---

# 口播剪辑

把用户提供的中文口播素材制作成可发布的抖音竖屏成片。强制执行“先方案、后剪辑”：收到素材后先分析并提交逐时间段分镜方案；只有用户明确确认方案后才能创建剪辑工程、改动画面或渲染成片。没有素材时只请求视频路径或附件，不得把历史样片当作本次素材。

## 必须调用的能力

实际制作时，先完整读取并遵守以下可用技能：

- `hyperframes:hyperframes`：合成、字幕、媒体轨道与视觉检查规则。
- `hyperframes:hyperframes-cli`：初始化、转写、检查、预览和导出。
- `hyperframes:gsap`：信息卡、画中画和转场动画。

添加语音同步文字时读取 HyperFrames 的字幕参考；制作多场景转场时读取其转场参考。方案审批规则见 [references/planning-gate.md](references/planning-gate.md)，视觉、动画和交付要求见 [references/editing-spec.md](references/editing-spec.md)。

## 工作流程

### 阶段一：分析与方案

1. 确认本次口播稿、口播视频、相关视频、图片、录屏和其他素材。保留源文件，不覆盖、不改写。
2. 检查所有媒体的时长、方向、分辨率、帧率、音轨、构图、人物位置、口播完整性和可用内容。
3. 转写中文语音并生成时间戳。不得使用 `.en` 语音模型。根据声音和上下文修正明显识别错误，但不核查或擅自改写事实、观点、人物、数字和日期。
4. 将口播稿、实际语音和素材逐项对齐，标记口误、重复、停顿、缺失素材及稿件与实录差异。
5. 按 [references/planning-gate.md](references/planning-gate.md) 生成完整分镜方案。每个内容段必须写明原片时间、预计成片时间、观点内容、画面模式、素材文件、信息卡、画中画、字幕、动效、转场和声音。
6. 向用户提交方案并等待明确确认。用户提出修改时先更新完整方案；不得把讨论、追问或局部认可视为开剪授权。

### 阶段二：确认后制作

7. 仅在用户明确表示“确认”“按方案剪”“可以开始剪辑”等同意后开始制作。
8. 按确认方案删除准备动作、口误、重复、无效停顿、明显口头禅和结尾找停止键等废片。必要时重排完整句子，但不得改变原意或制造虚假表达。
9. 按内容在人物全屏口播、重点信息科技卡片、全屏软件/网页/图片/视频加圆形人物画中画三种模式间切换。
10. 生成中文在上、英文在下的双语字幕。英文采用自然、简洁的意译，不机械逐字翻译。
11. 轻度处理人声，加入低音量背景音乐和极少量强调音效。不得让音乐压住人声。
12. 使用 [assets/xingxingdaren-logo.svg](assets/xingxingdaren-logo.svg) 完成品牌转场、角标或结尾页。只读取这个 Logo 作为品牌来源，不主动抓取个人网站。
13. 运行结构、版面、字幕、对比度和动画检查，完整观看导出文件后交付。

## 自主决策边界

- 优先使用用户提供的辅助图片；没有素材时使用文字、简单图形和抽象示意，不自行查找公开图片。
- 分镜方案必须得到一次明确的整体确认。确认后可在方案范围内自主完成制作；若需要改变观点、删除关键结论、替换主要素材或改变已确认的画面结构，必须再次说明并等待确认。
- 不使用真实 App 名称、平台 Logo、水印或仿冒品牌界面。真实录屏中无关的 Logo、账号、通知和隐私信息应裁切、遮盖或替换。
- 不生成乱码、不可辨认的伪文字或装饰性代码。界面文字必须真实、正确、可读。
- 任何动画都必须服务于阅读顺序，不以花哨程度作为目标。

## 交付物

- 剪辑开始前：包含原片时间、预计成片时间和逐段画面设计的完整分镜方案。
- 可直接发布的 1080×1920 MP4 成片。
- 烧录中英双语字幕的版本。
- 中英双语 SRT、纯中文 SRT、纯英文 SRT。
- 可继续修改的完整项目文件和本次素材目录。
