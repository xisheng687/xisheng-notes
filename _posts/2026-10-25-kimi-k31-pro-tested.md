---
layout: post
title: "实测Kimi K3.1 Pro是开源第一，但…"
date: 2026-10-25
---

Kimi K3.1 Pro出来几天了，我们先来快速过一遍官方的情况说明。

&nbsp;

&nbsp;

它是三个月前那个 K3 的升级版，2.8 万亿参数，上下文 100 万，并且能看图。

价格是输入 2 美元、输出 10 美元每百万 token，比 K3 便宜了三分之一，差不多是 Opus 5.5 的一半。

还有一个 Highspeed 版，官方说快 2 到 3 倍，价格当然也要跟着 2-3 倍地翻。

&nbsp;

第三方的综合榜单 Artificial Analysis 给了它 55 分，目前排名是全球第 4。

前面只有 Opus 5.5 的 58 分，Sonnet 5.5 和 Meta 的 Muse Wonder Full 的 56 分，GPT-6 Astra、Gemini 4 Argon 都排在它后面。

&nbsp;

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/body-01.jpg)

▲ 图来自 Artificial Analysis，K3.1 Pro 55 分，比 K3 涨了 11 分

&nbsp;

kimi说 11 月 4 日之前会放出完整权重。

想想看，这句话要是兑现了，最强的开源模型和最强的闭源模型，差距会从 12 分缩到 3 分。

Simon Willison 当天在博客里写了这么一句。

> This is the first time a (soon-to-be) open weight model has scored this highly against the frontier.
> 
> 这是第一次，一个（即将）开放权重的模型，在和最前沿模型的比较中拿到这么高的分。——Simon Willison，2026-10-23

&nbsp;

&nbsp;

kimi这次还做了件挺少见的事。

开源之前，它主动把训练数据里跟网络攻击有关的内容删掉了，自家的漏洞测试里，不删能做对 90.5%，删了是 81%。

当然，删了不等于没有，81% 还是远高于 K3 的 33.3%。

&nbsp;

现在，看下我的自己的几个实测吧。

&nbsp;

我要求三个模型做了一只送外卖的橘猫的游戏。

要求：只交一个 index.html，双击就能玩，有开始界面、计分、计时、失败重开，键盘和手机都能操作，音效要用 WebAudio 自己合成，做完还得自己开浏览器测一遍。

结果如下：

&nbsp;

&nbsp;

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/b_game_3way.mp4"></video>

Kimi 7 分 15 秒就交卷了。

Codex 用了 19 分钟。

Claude 用了 36 分钟。

&nbsp;

账单按各家官方 API 价格算，Kimi 花了 0.76 美元，Codex 差不多，0.75 美元，Claude 是 3.26 美元。

所以坦率的讲，Kimi 并不是三家里最便宜的，它和 Codex 一个价，只是比 Claude 便宜一大截。

额度上，Kimi 这一题用掉了 5 小时额度的七成左右。

&nbsp;

第二题，我换了个方向，不考游戏，考空间。

设计一个能 3D 打印的手机支架，给了 iPhone 17 Pro 的尺寸，靠背斜 65 度，底部留充电线口，轻点屏幕不能往后倒，还要算出重心。

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/b_stand_3way.mp4"></video>

▲ 希声实测，三家的支架模型放在一起转一圈，上方标了耗时、额度和 API 折算

&nbsp;

Kimi 的最朴素，一块底板、一个前挡、一块 65 度的靠背。

它做了 10 分钟，模型做好了，正准备出视频和说明书，额度没了。

Codex 的最大最结实，19 分钟，东西交得最全。

Claude 的最省料，21 分钟，还算了一下防倒，按它的计算，安全系数在 3 倍以上。

按 API 价格算，三家分别是 0.32、0.81 和 1.85 美元。

&nbsp;

本来还有第三题，让它读完 X 上 251 条夸它、骂它的帖子，给自己写一份测评。

没跑成。

额度在第二题中途就用完了。。

&nbsp;

说到这儿，就得聊聊这次最大的坑了——Kimi Code 的额度。

&nbsp;

首先，最低版本的套餐是没办法在 kimi code 里面使用的。

![](https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/body-02.png)

我买的是 99 块一个月的 plus 档。

第一次测试的时候，三个任务一起丢给它，思考档没动，就是默认的 max。

两分半钟以后，三个全停了，提示 5 小时的额度用完了。

一个文件都没交出来。。

&nbsp;

晚上额度刷新，我又试了一次。

这回换成 high 档，一次只跑一个。

小游戏完整做完了，7 分 15 秒。

手机支架做到第 10 分钟，又提示额度用完了。

这一轮按 API 价格算，一共 1.08 美元左右。

也就是说，99 块这档，一个 5 小时窗口，大概够它在 high 档下连续干 17 分钟。

想开着默认的 max 让它干大活，基本是不够的。

&nbsp;

一开始我还以为是自己用法不对。

去海外看了一圈，发现大家都差不多。

有人 5 小时的额度，提示词发出去 1 分钟就没了，什么都没做出来。

有人买了 699 档，开了快速模式，15 分钟跑光光。

&nbsp;

为什么烧得这么快？

看了下Kimi Code 最新版的配置，K3.1 Pro 默认就是最高的 max 思考档，而且强制思考。

它又特别爱拉子智能体帮忙，子智能体默认也跟着用 max，所以消耗如流水。

&nbsp;

想省额度，可以这么做：

1、平时把思考档从 max 调到 high，真正难的题再开 max。

2、它拉子智能体的时候，给子智能体换一个便宜点的模型。

3、中途切模型、切思考档，缓存会失效，切之前最好新开一个对话。

&nbsp;

吐槽完额度，我们再看下官方的演示，感受下 3d 能力的提升。

这次 3D 被官方放在了最前面，能在 Unity、Unreal、Godot 里做游戏，不用插件就能写 Blender 和 CAD 脚本，

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/a_official_palace.mp4"></video>

▲ 官方演示，K3.1 Pro 从头到尾生成的 3D 场景

&nbsp;

然后是有网友让它做一个 3D 网页，把一只机械手拆成 2317 个零件。

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/a_crystal_hand.mp4"></video>

▲ 视频来自 crystalsssup

&nbsp;

还有人用 kimi一句话做一架直升机，起飞、降落、零件拆开的爆炸视图、X 光模式、线框模式全都有，不到 15 分钟。

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/a_lumina_heli.mp4"></video>

▲ 视频来自 LuminaBench

&nbsp;

还有一道 Three.js 题，画一匹奔跑的马，这是三个模型的对比：

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/a_ai_screening_3way.mp4"></video>

▲ 视频来自 AI_Screening，从上到下依次是 Kimi、Opus 5.5、GPT-6 Astra

&nbsp;

综合总结就是：设计思路像 GPT，但多了一点 Anthropic 模型的审美。

&nbsp;

下面再看几个不同模型的对比。

做了一个鲸鱼跃出海面的场景，Kimi 花了 0.75 美元，Opus 5.5 花了 3.01 美元，Astra 2 美元，Gemini 4 Argon 2.3 美元。

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/a_bhavani_whale.mp4"></video>

▲ 视频来自 Bhavani_00007，四家同题

&nbsp;

做一座飘在云上的城堡，Opus 35 分钟，Kimi 44 分钟，原作者觉得还是 Opus 的界面更好。

&nbsp;

<video controls playsinline width="100%" src="https://xisheng687.github.io/xisheng-notes/assets/posts/2026-10-25-kimi-k31-pro-tested/a_sakata_castle.mp4"></video>

▲ 视频来自 sakatayasha，云上城堡同题

&nbsp;

&nbsp;

&nbsp;

最后，总结一下：

主要做 3D、小游戏、网页、数据可视化的，可以直接用，这几样它又快又好看。

写代码又在意钱的，走 API 按量付费更划算一些。

修线上 bug、写大工程，目前还是 Opus 更好用。

只想开个会员随便用的，记得先把思考档调到 high哦。
