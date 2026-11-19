# 双钻模型 · 第一钻：发现（Discover）与定义（Define）

> 调研日期：2026-11-19。范围：桌面网络调研（二手资料），尚未做一手用户访谈。
> 每条数据后标注了来源和可信度；标「厂商」的数字来自有利益相关的公司，只能当线索。

## 0. 结论先行

1. **真正被验证的痛点是「信息碎片化」和「低价值事务性负担」，不是「不会写」。** 截止日期散落在 Canvas、邮箱、课程大纲里，近半数学生因此错过过重要 deadline。
2. **「AI 用不用」已经不是问题，94% 的学生在评分作业里用 AI。** 差异化不在「能生成」，而在「本地、常驻、跨来源、懂我这学期所有课」。
3. **「降 AI 率」是一条正在关闭的赛道。** 检测器本身不可靠，高校正在从「查终稿」转向「查过程」（版本历史、口头答辩、课堂手写）。针对检测器做对抗，打的是上一场仗。
4. **「全自动代做 + 自动提交」有先例，结局是被平台方法务下架。** Einstein（号称全自动完成 Canvas 课程）收到 Instructure 的律师函后关站。
5. **推荐的产品定义：本地优先的「课程事务管家」**，自动化信息收集、整理、提醒、转写、复习；作业环节做「草稿与反馈助手」，人审后本人提交。

## 1. Discover：发散调研

### 1.1 用户与使用现状

| 发现 | 数据 | 来源 / 可信度 |
|---|---|---|
| AI 使用已近乎普及 | 95% 英国本科生用 AI，94% 用于评分作业；2024 年为 66% | HEPI/Kortext 2026，n=1054，可信 |
| 主要用途是理解而非代写 | 讲解概念 61%、总结文章 49%、找研究思路 40%、梳理结构 39% | 同上 |
| 学校开始官方供给 | 38% 的学生说学校提供 AI 工具（2025 年 23%，2024 年 9%） | 同上 |
| 体验两极 | 49% 认为 AI 改善了学习体验，16% 认为变差 | 同上 |
| 国内：期末集中赶工是主要动因 | 学生称期末作业与复习撞车，只能靠 AI 提速，甚至拼单买 AI 服务 | 新华网 2025，定性 |
| 国内：依赖度随年级上升 | 65.9% 遇到问题首选问 AI，大四明显高于大一 | 中青报等 2025，二手转述 |

### 1.2 痛点证据

| 痛点 | 证据 | 来源 / 可信度 |
|---|---|---|
| 截止日期分散导致漏交 | 47% 的学生因不知道截止日期错过重要 deadline；大一和一代大学生更严重 | Pathify 2025，**厂商**调查 |
| LMS 自身日历不完整 | Canvas 日历和 To-Do 会漏项；有老师不在作业上填 due date | Oregon State、LCC，定性 |
| 时间管理与动力 | 在线课学生自述最大困难是时间管理和动力 | PCC 小规模投票 |
| 期末拥堵 | 作业与考试复习集中在同一两周 | 新华网，定性 |

**缺口：** 没有找到专门针对「水课」的量化调查。这是需要一手访谈补的地方（见第 4 节）。

### 1.3 竞品与技术可行性

| 模块 | 现状 | 对我们的含义 |
|---|---|---|
| Canvas 数据接入 | 已有多个开源 Canvas MCP 服务器（vishalsachdev/canvas-mcp、bruchris/canvas-lms-mcp、DMontgomery40/mcp-canvas-lms），都用个人 Access Token | 不用自己造轮子；**风险：部分学校禁止学生生成 token** |
| 实时转写 | faster-whisper、WhisperLive、WhisperLiveKit 可全本地运行，带说话人分离 | 家用固定电脑跑本地模型可行；实时准确率取决于分块策略 |
| 学习类 AI 应用 | NotebookLM（免费/$4.99）、StudyFetch、Kiwi AI（$9.99）、ChatGPT（$20）等，都是「你上传，我处理」 | 没有一个是常驻、主动、跨 Canvas+邮箱的；这是空位 |
| 全自动代理 | Einstein 被 Instructure 发函下架；Perplexity CEO 公开对用 Comet 做 quiz 的学生说「绝对别这么干」；Instructure 自己推出 IgniteAI Agent | 平台方会用法务和技术手段（SSO+MFA、锁定浏览器）对抗代登录代理 |

### 1.4 风险环境

| 风险 | 证据 | 来源 |
|---|---|---|
| 检测器误判严重 | 7 款检测器把 61% 的非母语者托福作文判为 AI | Stanford 2023（未测 Turnitin） |
| 国内 AIGC 率硬门槛 | 复旦禁止 AI 生成论文正文；川大某学院要求 AIGC 率低于 15% 才能答辩 | 新华网、凤凰网 |
| 专家质疑检测 | 判定依据模糊、系统间结果不一致，「黑匣子」 | 凤凰网、网易 |
| 查处在上升 | 英国 2023-24 年近 7000 起已证实的 AI 作弊，5.1‰，前一年 1.6‰ | Guardian FOI 调查 |
| 考核方式在变 | 口试、手写考试回归；「看过程不看成品」；版本历史 + AI 使用声明 | THE、eWeek |
| 课堂录音受限 | 多校规定录音仅限个人学习，不得上传第三方 AI；禁止偷录；各地法律对同意的要求不同 | Glasgow、Melbourne、Colorado |

## 2. Define：收敛出的洞察

**洞察 1｜学生缺的不是写作能力，是一个「替我盯着」的人。**
最硬的数据是漏 deadline，不是写不出来。Canvas 自己的日历都会漏项。一台常驻家里的电脑恰好适合做这件事：持续轮询、合并多来源、推到手机。

**洞察 2｜「水课」的本质是投入产出比低，学生要的是把投入压到最低且不出事。**
「不出事」和「省时间」同等重要。任何让学生背上学术不端风险的功能，都在破坏这个核心价值。

**洞察 3｜检测器不准，对学生是双向风险。**
自己写的也可能被误判（非母语者尤其如此，这正是留学生群体）。所以有价值的不是「把 AI 文本伪装成人写的」，而是「能证明这是我写的」：保留草稿版本、写作过程记录、资料来源。这和高校转向过程性考核的方向一致。

**洞察 4｜对抗检测是军备竞赛，且赛场正在被换掉。**
学校的应对不是买更强的检测器，而是口头答辩和过程证据。一篇检测率 0% 但本人讲不清楚的文章，在答辩环节照样出事。

**洞察 5｜「本地」是真正的差异点。**
课堂录音不得上传第三方 AI 是多所学校的明文规定。本地转写 + 本地存储恰好合规，云端竞品做不到。

**洞察 6｜全自动提交是平台方的红线。**
只读同步（看作业、看公告、看日历）用的是官方 API 的正常用途；代登录、代答题、代提交则会触发法务和封号。

### 问题定义（How Might We）

> 我们如何让一个同时修多门低投入课程的学生，**每周只花几分钟确认**，就不漏任何截止日期、不漏任何重要通知、带着整理好的材料进入作业和考试，**并且不承担任何学术诚信风险**？

## 3. 需求优先级与范围

| 原始设想 | 证据支持 | 建议 |
|---|---|---|
| 自动检测 email + Canvas，信息存本地 | 强（痛点最硬，技术现成） | **MVP 核心** |
| 自动整理、提醒、预约，手机一点确认 | 强 | **MVP 核心** |
| 网课 OCR + 实时转写 | 强（本地是优势） | **第二阶段**；需遵守所在学校的录音规定 |
| 自动组织考试复习 | 强（期末拥堵） | **第二阶段**，基于转写和课件生成提纲、题库 |
| 海量 skill | 中 | 架构上支持插件，但先做深三四个 |
| 自动写作业 | 需求真实，但全自动有风险 | **改为**：拆解题目要求、整理材料、出提纲和草稿、对照评分标准给反馈；本人修改并提交 |
| 自动上课 | 无证据支持，风险高 | **改为**：直播/录播课的转写和摘要，告诉你「老师说了什么、有没有点到作业和考试」 |
| 极致降低 AI 识别率 | 赛道在关闭，反而增加风险 | **不做**；替换为「写作过程存证」（版本历史、来源记录、AI 使用声明草稿） |

### 关于范围的说明

有三项我不会参与设计或实现：**针对 AI 检测器的规避**、**无人审核的代写代交**、**代签到/伪造出勤**。这三项的用途就是让学校误以为工作是学生本人完成的，「仅供研究」的标注不改变做出来的东西是什么。上面的调研也说明它们在产品上站不住：先例被下架，考核方式在绕开检测器，而事故成本由用户承担。

表里的替代方案保留了同样的省时目标。

## 4. 待验证假设（进入第二钻之前）

二手资料回答不了的问题，需要 5–8 个目标用户访谈：

1. 「水课」在用户口中具体指哪类课？每周实际耗时多少，耗在哪一步？
2. 最近一次漏交或差点漏交是怎么发生的？信息当时在哪个渠道？
3. 用户的学校是否允许学生生成 Canvas Access Token？（决定技术路线）
4. 用户是否愿意让家里电脑 24 小时开机？能接受的配置成本是多少？
5. 手机端「一点确认」的边界：哪些事愿意全自动，哪些必须过目？
6. 用户所在学校对 AI 使用和课堂录音的具体规定是什么？

## 5. 来源

- [HEPI/Kortext Student Generative AI Survey 2026](https://www.hepi.ac.uk/reports/student-generative-ai-survey-2026/)
- [The Decoder：95% of UK students now use AI](https://the-decoder.com/95-of-uk-students-now-use-ai-and-their-experiences-couldnt-be-more-divided/)
- [Pathify 调查：近半数学生因数字碎片化错过截止日期](https://www.edtechinnovationhub.com/news/pathify-survey-finds-nearly-half-of-us-college-students-have-missed-deadlines-due-to-digital-fragmentation)
- [Oregon State Ecampus：Canvas 学生体验研究](https://ecampus.oregonstate.edu/faculty/inspire/?p=5305)
- [LCC：学生使用 D2L 的三大困难](https://elearning.lcc.edu/instructors/student-challenges-fall-2024.html)
- [PCC QuickPoll](https://www.pcc.edu/online/2021/01/quickpoll-results-what-have-you-struggled-with-in-one-of-your-current-classes/)
- [新华网：高校 AI 使用规定（2025-01）](https://www.news.cn/tech/20250113/3d1673e3150b46198b0bcaa2f8493dac/c.html)
- [新华网：大学生用 AI 赶作业（2025-07）](https://www.news.cn/local/20250702/7d0f562a4efe424cb3a9f46c85319707/c.html)
- [凤凰网：AIGC 检测争议](https://news.ifeng.com/c/8trxZ6ZBOLt)
- [网易：AIGC 检测「黑匣子」](https://c.m.163.com/news/a/KV57JS980514BE2Q.html)
- [Liang et al.：GPT detectors are biased against non-native English writers](https://arxiv.org/pdf/2304.02819)
- [The Markup：AI 检测工具误判国际学生](https://themarkup.org/machine-learning/2023/08/14/ai-detection-tools-falsely-accuse-international-students-of-cheating)
- [eWeek：英国高校 AI 作弊案例（Guardian 调查）](https://www.eweek.com/news/uk-universities-ai-cheating-guardian/)
- [The Register：UK students and AI cheating](https://www.theregister.com/2025/06/16/university_ai_cheating/)
- [Anna Mills：The time to reckon with AI agents](https://annamills.substack.com/p/the-time-to-reckon-with-ai-agents)
- [CVC：Safeguarding Academic Integrity in the Age of Agentic AI](https://www.cvc.edu/wp-content/uploads/2025/11/Safeguarding-Academic-Integrity-in-the-Age-of-Agentic-AI.pdf)
- [Yahoo：Agentic browsers present risks to universities](https://www.yahoo.com/news/articles/cheating-beyond-chatgpt-agentic-browsers-190006839.html)
- [Instructure IgniteAI Agent](https://www.constellationr.com/index%2Ephp/insights/news/instructure-launches-igniteai-agent-canvas-builds-amazon-bedrock)
- [THE：Focus on process, not end product](https://www.timeshighereducation.com/node/745917)
- [eWeek：口试和手写考试回归](https://www.eweek.com/news/colleges-turn-to-oral-exams-ai-disruption/)
- [canvas-mcp（PyPI）](https://pypi.org/project/canvas-mcp/1.1.0/)
- [bruchris/canvas-lms-mcp](https://mcpservers.org/servers/bruchris/canvas-lms-mcp)
- [DMontgomery40/mcp-canvas-lms](https://mcpservers.org/en/servers/DMontgomery40/mcp-canvas-lms)
- [faster-whisper](https://raw.githubusercontent.com/SYSTRAN/faster-whisper/master/README.md)
- [WhisperLive](https://github.com/collabora/whisper-live)
- [Glasgow：Recording of Teaching Policy 2026-27](https://www.gla.ac.uk/myglasgow/learningandteaching/news/headline_1289844_en.html)
- [Melbourne：学生使用 AI 转写工具的管理](https://academicintegrity.unimelb.edu.au/staff-resources/managing-student-use-of-ai-assisted-transcription-and-translation-tools)
- [Colorado：课堂录音规定](https://www.colorado.edu/disabilityservices/accommodations/note-taking-accommodations/student-parameters-recording-class-lectures)
- [YouLearn：2026 AI 学习工具盘点（厂商）](https://www.youlearn.ai/blogs/best-ai-tutor-apps-college-students-2026)
