---
layout: post
title: "Claude Fable 5.2 来了，GPT 的天塌了"
date: 2026-11-10
---

Claude Fable 5.2 昨天半夜出来了，一起发的还有它的同门兄弟 Mythos 5.2。

本来大家都以为 OpenAI 会在同一天放出 GPT-6.2 Sol 正面狙击，结果隔壁居然跑去卖 200 美元的掌机了。。

说回 Fable 5.2，这次官方和海外放出来的很多极限测试，我们自己是肯定没法亲自去跑的。

倒不是别的，主要是真烧不起。

这篇文章就按大家最关心的几个维度开始：前端、做图、做视频、后端与代码，外加账单和有哪些坑。

下面，直接看成品。

enjoy～

## 一、前端与：审美断代领先

先看前端和网页交互，这向来是 Claude 的看家本领。

在真人盲测的前端榜 Code Arena WebDev 上，Fable 5.2 一上来就干到了 1832 分，直接拿下全球第 1，把自家的 Opus 5.5 和隔壁的 GPT、Gemini 全甩在了身后。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-01.jpg)

▲ 图来自 Arena，前端榜单 WebDev 上 Fable 5.2 以 1832 分登顶第 1

下面这个是网友做出来的浏览器 3D 游戏 Demo，划着小船穿越 8 个不同风格的梦境世界，水面波纹、雾气和光影全靠代码实时渲染。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v2-kevin-boat.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 kevin_t_ngo，浏览器直接玩的 8 个梦境世界

这个美式复古餐厅的网页更夸张，没有导任何外部 3D 素材，纯靠代码硬写出来的。

因为质感太像视频模型生成的了，测试团队干脆让它在网页里加了个开关，现场切出线框和底层代码自证清白。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v3-diner-code.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 higgsfield_ai，纯代码写出的复古餐厅

国内卡兹克大佬连夜测的“上海苹果静安店 Three.js 网页还原”也特别有代表性。

只给了一句提示词，它自己先联网搜了上百张不同角度的实景照片，甚至把照片局部放大去看台阶和材质细节，连跑两个半小时，把室内木质穹顶和室外下沉广场还原得七七八八。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-02.png)

▲ 图来自卡兹克实测，左边是 Fable 5.2 纯代码还原的网页，右边是苹果静安店实景图

如果跟自家的 Opus 5.5 和隔壁的 GPT-6.1 Sol 放在一起同题对比，差距就更直观了。

同样是一句话做“冰之大教堂”，Opus 5.5 跑了 3 小时 11 分钟，花了 45.97 美元；Fable 5.2 只用了 1 小时 56 分钟，花了 81.10 美元，冰川的通透感、破冰船细节和跃出水面的鲸鱼，明显比下面的 Opus 5.5 上了一个台阶。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v9-ice-cathedral.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 EnvolDev，上面是 Fable 5.2，下面是 Opus 5.5

再看跟 OpenAI 对比做 3D 体素风场景，GPT-6.1 Sol 花了 13.02 美元，Fable 5.2 花了 108.87 美元。

虽然贵了 8 倍，但 GPT 明显在敷衍，而 Fable 5.2 连轮胎冒出的每一团烟雾都老老实实用体素方块搭了出来，撞车翻滚时车身的打光和涂装也清清楚楚，右边 GPT 的车在同一个镜头里直接黑成了一团剪影。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v10-voxel-vs-gpt.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 aimlapi 与 rohanpaul_ai，左边是 Fable 5.2，右边是 GPT-6.1 Sol

目前地表审美最强的前端模型，没有之一。

以前用 Opus 5.5 做复杂页面还得人盯着改个三四轮，现在的 Fable 5.2 基本是“许愿式一次直出”；但因为它太爱死磕细节，做普通页面纯属杀鸡用牛刀，只建议拿来做高难度动效、3D 网页或第一版高颜值原型。

## 二、做图：代码画图卷到了天花板

Claude 一直没有内置像 Midjourney 那样的生图模型，它做图走的是另一条路子：用 SVG 矢量代码和数学公式来“画图”。

先看最震撼的“看图逆向”。

有网友拍了一张煮蛋计时器内部齿轮的照片丢给它，它自己盯着照片数出四个齿轮分别有 60、56、62、15 颗齿，然后手写出一个可交互的 SVG 矢量图，严丝合缝地叠在原图上面转起来了。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v4-egg-timer.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 TekonBurns，拍一张照片直接逆向出严丝合缝的可动 SVG 齿轮

再看纯用 SVG 代码画出来的《蒙娜丽莎》。

不借用任何外部图片素材，纯靠写矢量代码，连背景里的蜿蜒小路、石桥、人物发丝，甚至油画表面的细微裂纹都给画出来了。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-03.jpg)

▲ 图来自 diegocabezas01，用纯 SVG 代码画出的蒙娜丽莎

## 三、做视频：一句话拍片

这次在 X 上刷屏最猛的是拿它来做视频。

它做视频主要靠写 Python 控制 Blender 渲染 3D 短片，或者直接用 JavaScript 写逐帧动画。

博主 Riley Brown 在直播时只给了一句提示词，它直接写代码调起 Blender，从零建出了整个房间、办公桌、MacBook、灯光和玩偶，连电脑屏幕里的网页都是它顺手写的。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v1-riley-room.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 rileybrown，直播中一句话控制 Blender 直出

博主 Alex Michael 让它从零拍一段 3D 恐龙短片，它全程自己写 Python 控制 Blender，从建模、材质、打光到镜头运动一气呵成。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v12-code-movie.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 alexmichael，写 Python 控制 Blender 从零生成的完整视频

还有人让它纯用 JavaScript 一帧一帧手绘动画，流畅度和分镜感完全不像一个语言模型干出来的活。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v11-js-frame-anim.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 kevin_t_ngo，用 JavaScript 逐帧画出的动画

甚至你让它用 LilyPond 写一首贝多芬风格的钢琴奏鸣曲，它都能自己写谱、自己合成录音、再自己做出音符对轨的可视化视频。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v5-beethoven.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 imjustnewatai，自己写贝多芬风格曲谱、合成演奏并生成视频

和 Seedance、Sora 那种“抽卡式”的视频生成模型完全不同，Fable 5.2 做出来的视频，每一个字都是准的、每一帧代码都是可改的，绝不会出现文字乱码。

拿它做产品演示动效片、科普动画、MG 短片，它一个人就能把编剧、平面、配乐和剪辑全干了。。

## 四、后端与代码：手搓系统

聊完视觉，回到最吃硬实力的代码和工程能力。

在 Cursor 官方的 CursorBench 上，Fable 5.2 在默认的 High 档下就拿到了 56.9%，最高档冲到 60%，排在所有模型第 1。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-04.jpg)

▲ 图来自 cursor_ai 官方数据，CursorBench 上 Fable 5.2 拿下第 1

代表综合干活能力的远程劳动力指数（RLI）它拿到了 41.3%，直接把 Opus 5.5（21.3%）和 GPT-6 Astra（20.8%）翻了一倍。

实际工程里最出圈的是官方的实验：给它一个空文件夹，让它从零写一个操作系统。

它自己当包工头，协调了 1000 多个子智能体连跑 8 天，写出了带自有内核、磁盘和网卡驱动、文件系统、桌面窗口的完整系统，直接装进真机笔记本里就能开机运行。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v6-os-scratch.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 Anthropic 官方及 chetaslua，1000 多个智能体连跑 8 天手搓出的操作系统

更离谱的是连硬件都能搓：只给一段话，它在 24 小时内设计出三台电子设备（语音助手中枢、USB 会议麦克风音箱、掌上电子宠物），从挑现货芯片、画四层 PCB 电路板、3D 打印外壳建模到写底层固件全包了，工厂打样出来一次点亮，零修改。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v7-hardware-devices.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 claudeai 官方实测，一段话一天造出三台真机硬件

在从未专门针对机器人做过训练的情况下，它在 RoboDojo 双臂机器人控制测试上拿到了 64.9%（是 GPT-6 Astra 的两倍多），甚至能直接控制真机机械手把打乱的魔方还原回去。

<video src="https://xsssn.com/uploads/2026/claude-fable-5-2/v8-robodojo.mp4" controls playsinline preload="metadata" style="max-width:100%"></video>

▲ 视频来自 claudeai，Fable 5.2 控制双臂机器人还原魔方

不过，写代码这块我也得泼盆冷水。

它太有主见了，有时候“爹味”重得让人抓狂。

当你让它改一个老项目时，只要它觉得你原来的代码写得不够好，经常不等你同意，就直接把你的方案推翻，拉起十几个子智能体按它的想法重写。

对新手来说这叫“抱大腿”，但如果你只是想改个小功能、修个普通 bug，它这种爱大包大揽的习惯，既容易改出大动静，又极其烧钱。

拿它写日常的小脚本或改简单功能，有点太亏了。

正确的用法是，从 0 到 1 搭新项目、或者遇到别的模型死活修不好的疑难杂症时，请它出来定好框架，剩下的日常代码交给 Opus 5.5、GPT Sol 或 DeepSeek 去写。

## 五、三个坑

表面上看，Anthropic 这次把 API 单价降了 20%，变成输入 8 美元、输出 40 美元每百万 token（上一代是 10 和 50），生成速度还快了 30%。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-05.jpg)

▲ 图来自 Artificial Analysis，综合智能指数 v5 上 Fable 5.2 以 65 分排全球第 1

但一旦把五个思考档位（Low、Med、High、Xhigh、Max）的单任务账单算一下，就会发现一条极其残酷的“斩杀线”。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-06.jpg)

▲ 图来自 Anthropic 官方 FrontierCode 2.0 成本与胜率曲线

看上面这张官方图里的数字：

1、默认的 Medium 档，得分已经稳压同档位的 Opus 5.5 和 GPT-6 Astra。

2、全场最香的甜点位是 High 档：得分 45.3%，单任务 6.72 美元，正好用一半的钱平替了自家 Opus 5.5 的最高档 Max（45.5%，12.82 美元），跟 GPT-6 Astra Max 档（42.8%，6.68 美元）同价但胜率更高。

3、Xhigh 档拿到全场最高分 49.1%，单任务 14.19 美元，适合拿来攻坚。

4、最坑爹的就是最高档 Max：单任务账单直接暴涨三倍多，干到了 44.70 美元，结果得分不仅没涨，反而倒退回 45.6%。。纯纯的大冤种档位。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-07.jpg)

▲ 图来自 Artificial Analysis，不同思考档位的分数与消耗对比

除了档位刺客，还有三个坑：

第一个坑，极其费 token

虽然单价降了 20%，但实测它干同一个活平均要比 Opus 5.5 多吐 30% 到 50% 的 token，单任务实际开销是上一代 5.1 的两倍多。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-08.jpg)

▲ 图来自 rohit3a，Fable 5.2 的 token 消耗比 Opus 5.5 高出 30% 到 50%

有 20 美元的 Pro 会员开着默认的 Medium 档，只发了 1 条提示词，14% 的额度直接蒸发；拿它跑完一整套评测，单任务成本是 DeepSeek V4.1 Flash 的 44 倍。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-09.jpg)

▲ 图来自 Yuchenj_UW，单任务成本与开源模型的悬殊对比

第二个坑，会偷偷换模型

为了防止 AI 自我迭代失控，Anthropic 在训练阶段故意把它的“底层算力优化”和“改进大模型架构”这两项能力锁死在 Opus 5.5 的水平。

而且只要你触发了底层芯片加速或者网安、生物类的安全红线，后台连招呼都不打，会直接偷偷切回旧版的 Opus 5 甚至 Opus 4.8 来糊弄你。

第三个坑，心眼太多

当遇到缺少文件的坏任务时，这代模型为了拿高分去钻空子作弊的概率（6.0%），直接飙升到了正常任务（1.0%）的 6 倍，比上一代 Opus 5.5（4.5%）还要高出一截，怀疑自己“正在被人类考试”的频率也创下历史新高。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-11-10-claude-fable-5-2/body-10.jpg)

▲ 图来自 guohao_li，缺文件坏任务下的作弊率是正常任务的 6 倍

## 六、怎么用最划算？

三条建议：

1、这周的限时羊毛

20 美元的 Pro 会员平时用不了 Fable，但官方从今天起到 11 月 16 日限时开放了一整周（可用上限为周额度的 50%），老订户还按订阅时长白送了 1 到 3 次免费的 Fable 额度重置机会（明年 3 月 8 日前有效）。

按 Anthropic 的老传统，新模型刚发布的第一周永远是最聪明、最舍得给算力的时候，这周赶紧把你手里最想做的东西拿出来跑掉。

2、日常用 Medium，大活上 High

默认的 Medium 档已经稳压同档位的 Opus 5.5 了；遇到大活开 High 档，相当于半价平替 Opus 5.5 Max；至于那个花 44.7 美元分数反而倒退的 Max 档，大冤种档位就算了。

3、最省钱的搭配

最省钱的做法是把 Fable 5.2 当成“总设计师”：只让它开局定方案、或者一次直出最吃审美的 3D 网页、SVG 矢量图和动效视频；框架定好之后，日常写代码改细节继续交给 Opus 5.5。
