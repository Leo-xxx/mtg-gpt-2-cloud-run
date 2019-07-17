## 你还在氪金抽卡？高玩用GPT2自己生成SSR卡

[机器之心](javascript:void(0);) *5天前*

机器之心报道

**机器之心编辑部**







> 集换式卡牌类游戏绕不开的就是抽卡。为了一张卡面精美、效果拔群的卡牌，无数玩家献祭了自己的钱包。而最近，一位机器学习开发者开源了万智牌的卡牌生成器，玩家只需要指定名称就可以生成卡牌，其中不乏稀有牌。



![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16ktibwKxiaYtFmVbWjPJicNdn8iabHUqhhPg3OVFdXVrX8yDePbxrM7OeXiaqA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

玩过集换式卡牌类游戏的读者都知道，卡牌的效果决定了战斗力的强弱，越是稀有的卡（如 SSR）越有着更强的效果。但是，抽不到稀有的卡牌也让无数玩家心碎。近日，机器学习爱好者用 [GPT-2](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650765628&idx=1&sn=e5744765710c17e1d887b3f2b505eb2f&chksm=871abd42b06d3454e784d2baf5dc61a62af81f35695c93d2cc33d775eb5e1f1a826098ad6e5b&scene=0&xtrack=1&key=2f4703df4564706a68dde224f7cc0ec9ce794b26738e8297981d7263bbeb08592140c486ffb54641e1fe91b72e588720ea9ceab3aaed93bdc6789d0c9a8be7b79916a294af266d54e02a1ef29042afe1&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060739&lang=zh_CN&pass_ticket=iqn5fxyAYAEcbOWN8K0hTmIdnQAEbGoAMytUHUJn7mS3BliHEI0JRQI4B417Pox7)制作了一个万智牌生成器。玩家只需要指定卡牌名称，机器就可以自动生成牌面、效果、稀有度等信息。

项目作者 Max Woolf 毕业于卡内基梅隆大学，目前担任美国新闻聚合网站 BuzzFeed 的数据科学家，也曾在苹果就职。他已经提供了一个网站，有兴趣的玩家可以生成自己的万智牌卡牌。经过尝试，笔者发现出稀有牌的数量比游戏抽卡出的多很多。

- 生成器网址：https://minimaxir.com/apps/gpt2-mtg/
- 项目地址：https://github.com/minimaxir/mtg-gpt-2-cloud-run

**什么是万智牌**

万智牌（Magic: The Gathering）是著名的卡牌类游戏，类似的游戏有「炉石传说」。进行游戏的双方各自有一套牌组。游戏开始时，双方各有 20 点「生命」。双方打出牌，目标是使对方输掉这盘游戏。双方可以利用牌面上的效果将对方的「生命」降至 0 或以下，或迫使对手的牌库没有牌可抓，或牌手累积 10 个以上的中毒标记，或利用特殊咒语。

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16kt8HwVlkxE2iaSyx4TzLuWmkqPsVrhtLWxMvu2jyKs4JVPp0iaJFibdyVrw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)
*万智牌的一部分卡牌。*

卡牌是万智牌游戏的核心，由以下几部分组成：

- 卡牌名称：位于牌的左上角。
- 施法费用（Mana）：位于牌的右上角。表示需要施放的法术力。
- 卡牌插画：位于牌的正中。
- 卡牌类型：位于牌的插画下方靠左的位置。万智牌中有七种基本类别：「Land」、「Creature」、「Artifact」、「Enchantment」、「Planeswalker」、「Permanet」、「Sorcery」、「Instant」
- 稀有度：位于类别栏的右侧的标志，表示此牌的稀有程度。（金色代表「Rare」，银色代表「Uncommon」，黑色代表「Common」，不同版本可能有更稀有的卡牌）
- 效果描述：用于描述这张卡牌的效果。
- 力量和防御力属性：仅属于「Creature」这个类别的牌具有，位于牌的右下角，由斜线分开的两个数字表示，表现出该生物的力量和防御力（如：「3/3」表示 3 的力量和 3 的防御力）。
- 所属颜色：类似于阵营，图标会出现在施法费用旁边。一共有五种，见下图：

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16ktS9ycwSZgLfYtiaoKKYiaaVWmYJyJmcaNiabnASXugB1KN7u76dHOKAdaA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**稀有卡牌一键生成，只要几个词**

项目作者在 Reddit 中提到，这个项目可以自动生成万智牌卡牌，而玩家只需要输入卡牌的名字，而卡牌类型和施法费用可以自定义或交给机器决定。大约需要十几秒，机器就会生成一张新卡，包括卡牌插画、稀有度和卡牌效果的文字描述。

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16kt45dVLU0bDtTOPlpgbUVWh6atdg9cTzYchSTXeg6XibXmAvWgUwV1Czg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)*在左上角的框中填入卡牌名称，玩家可自定义卡牌类型（Card Type）和施法费用（Card Mana Cost）或留空。**机器会在右侧自动生成一张新的卡牌图片。*

作者提供了一些例子，比如：

Krovikan Vampire（寇维肯吸血鬼）

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16kt5InSDCLkLkqgicHic2iaKXkKVHial36uYjwHSvsxUuwN8VWHpbyfgbxaPQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这是一张 Uncommon 的卡牌，类型是 Creature 中的吸血鬼，还有出牌时的效果。牌面右上角则有施法费用、颜色等信息。从效果描述上来看，当这张牌入场或攻击时，其获得+2 的力量和+0 的防御力，直到回合结束。

这些信息都是由机器生成的，效果的描述和卡牌名称能够很好的搭配，行文也足够连贯。

机器之心也尝试生成了一些卡牌：

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16ktYutQVCoPmcTCDeibqCrDKJBeHryibfPFAwRZBGHPWm9HOERUChvzgulQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)*「火手」。*

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16kt8mUBwcj3mKiaOhET0hsnl6lOHBClzSBkhFTenrjELLdQ4hLtdkGecPw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)*「自然低语」。*

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16ktERERAUVbPpC8pPicGPmqdGj7ibc8fhBHmqOibyicG21SLoW6xSHgkJKuBA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)*「闪电獠牙」。**惊喜的是，有时候可以生成「Rare」稀有度（右侧为金色）的手牌。*

从实验来看，机器可以根据卡牌名称提供该种名称下类似的效果。比如类似火「Fire」的词语更偏向于产生带有伤害效果的手牌。而自然「Nature」这样的词语更偏向于获得增益效果。

**GPT-2：****卡牌生成器**

根据作者的描述，实现玩家制卡背后的技术是 GPT-2。

GPT-2 是 OpenAI 于 2018 年提出的一种基于 Tranformer 的预训练语言模型。Transformer 是一种流行的注意力机制，在 BERT 预训练语言模型中也有使用。

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16ktuwMLqPe9tDpseLl1dFAqsGeOKibiayYibCpManBRotNIvX8B1pzcViabtg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

在预训练 GPT-2 时，模型输入为无标注的语料，训练目标为预测一句话中的下一个字。相比于 BERT，GPT-2 增加了 Transformer 层数，采用了更多、更宽泛的语料进行训练，达到了更好的效果。

发布之初，由于担心被滥用，OpenAI 仅开源了「缩水版」的 GPT-2-simple 版本，仅有 117M 的参数量，而真正的 GPT-2 参数量达到多达 15 亿。

即使是 GPT-2-simple，它的效果也是惊人的。已有使用 GPT-2 生成假新闻的实现。也有很多人使用 GPT-2 进行更多的实验，OpenAI 自己也用 GPT-2 制作了一个 AI 音乐生成器。

在本项目中，作者使用了 GPT-2 117M，即最早开源的 GPT-2-simple。模型训练了 6500 步，在 P100 GPU 上耗费了两个小时。

作者表示，由于训练量较小，GPT-2 在卡牌名称和效果上出现了过拟合的情况。超参「Temperature」在 0.7 和 1.0 时，生成的卡牌比较普通，1.2 时，网络开始生成自己的规则和卡片，达到 1.5 和 2.0 时，生成的卡片类似于卡牌生成网站 MTGCardsmith。

目前项目已经开源，作者提供了生成卡牌效果和图片的 API。

**GPT-2 效果怎么样**

其实用 GPT-2 生成文本已经是非常通用的做法了，如果第一次看到它生成的文本，那么肯定会被惊艳到。似乎 GPT-2 依靠语言模型已经能生成非常「合理」的段落了，甚至我们都不太能确定它到底是机器写的还是人类制作的。

如下所示为机器之心尝试用 GPT-2 中 3.45 亿参数量的大模型做预测。即使我们每次都给相同的前提，模型也会生成完全不同的故事。在下面的例子中，我们发现 GPT-2 生成的样本还是非常合理的，甚至它还会生成一些不存在的 GitHub 地址。

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW8wSp1suAZaTbWWZK6n16kt3IZKNticnNAL3IMXyeib46RlkwkNvfxPDojiab4sN0QATX9ramztfRibHw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

如此神奇的模型可以源源不断生成各种各样的卡牌。考虑到作者已开源了项目代码，也许更换数据，你也可以为自己的手游或桌游生成超高稀有度的卡牌了。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/KmXPKA19gW9fMDBEUu6zbFUBohOOko5VUASOzDL6soyeeZPWibMic2Yj8VdNAfJNnrz1kyvSiaAG8xZiak8GymGyOw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**市北·GMIS 2019**全球数据智能峰会于**7月19日-20日**在上海市静安区举行。本次峰会以**「数据智能」**为主题，聚焦最前沿研究方向，同时更加关注数据智能经济及其产业生态的发展情况，为技术从研究走向落地提供借鉴。

本次峰会设置主旨演讲、主题演讲、AI画展、「AI00」数据智能榜单发布、闭门晚宴等环节，已确认出席嘉宾如下：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/KmXPKA19gWibBUIn1BvtZgiarCrY3mUb47DbC39DL8KRg9rGic7b5RzibUEZtZkhszRKYjE0dNLianOSZg5lEw0SnbQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

我们为广大学生用户准备了最高优惠的学生票，点击**阅读原文**即刻报名。

[阅读原文](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650765628&idx=1&sn=e5744765710c17e1d887b3f2b505eb2f&chksm=871abd42b06d3454e784d2baf5dc61a62af81f35695c93d2cc33d775eb5e1f1a826098ad6e5b&scene=0&xtrack=1&key=2f4703df4564706a68dde224f7cc0ec9ce794b26738e8297981d7263bbeb08592140c486ffb54641e1fe91b72e588720ea9ceab3aaed93bdc6789d0c9a8be7b79916a294af266d54e02a1ef29042afe1&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060739&lang=zh_CN&pass_ticket=iqn5fxyAYAEcbOWN8K0hTmIdnQAEbGoAMytUHUJn7mS3BliHEI0JRQI4B417Pox7##)







微信扫一扫
关注该公众号