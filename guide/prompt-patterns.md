# 提示词写法拆解

aiMakeVideo 的 showcase 里有两种完全不同的提示词。看懂这个区别，比背 100 条模板有用。

| 类型 | 词数 | 预算花在哪 | 例子 |
|---|---|---|---|
| **动作序列型** | 189–215 词 | 剧情、数量、动作编排、否定约束 | Volcano Forge Escape、Maglev Train Duel、Neon Rooftop Chase、Underwater Temple Heist |
| **风格描述型** | 26–44 词 | 光、光学、材质、商业调性 | Cliffside Silk Walk、Lumière Perfume Orbit |

**注意一个反直觉的点**：短的那种**也写运镜**（`slow lateral tracking shot`、`slow orbit`）。区别不在写不写镜头，而在**写不写动作编排**。

---

## 一、动作序列型：8 段结构

拿 [Volcano Forge Escape](../showcase/text-to-video.md) 拆开看，它是 8 个固定段落拼起来的。

### 1. 先定画质和镜头

> Photoreal live-action fantasy escape through an active volcanic forge cavern, crisp high-resolution cinema detail, ember heat haze kept optically sharp, clean HDR contrast, **one wide lens and one uninterrupted controlled handheld pursuit shot**.

三件事一次说完：**photoreal**（写实）、**cinema detail**（画质）、**一个镜头不断**（`one uninterrupted … shot`）。最后这个是关键——它从根上堵死"AI 自己剪成七八个镜头"。

### 2. 把主角钉死

> The smith-mage is a muscular North African woman, late 20s, shaved sides with dense curls, glowing ember freckles, soot-streaked bronze armor over ash linen, one living molten hammer in her right hand. **Keep one identical smith-mage throughout.**

年龄、体型、发型、服装、手里拿什么，全写清楚，再加一句 `Keep one identical X throughout` 锁住。不写这句，第 3 秒就换人。

### 3. 给出精确数量，并且指定最后一个

> **Exactly 5** distinct lava constructs emerge; **construct 5 is** a towering slag titan with a chain-anvil.

"5 个"是数字，"第 5 个是泰坦"是钩子。视频需要一个终点，否则会一直平铺下去。

### 4. 用否定句堵住模型最爱偷懒的地方

> **Never reuse** a construct. Every hammer blow hits **exactly one** target. Show 5 separate contacts. **No multi-target smash.**

模型默认会"一锤打一片"，因为那样省力。你要"一锤一个"，就得写 `exactly one` + `No multi-target`。**否定句在这个体系里和肯定句一样重要。**

### 5. 把动作轮着排一遍

> **Rotate** overhead forge strike, lateral quench-smash, vault over magma rivulet, ground-spike kick, and final titan knee break.

五个动作写成一个列表。不写的话，5 个镜头会长得一模一样。

### 6. 规定转场怎么发生

> Every relocation: micro-anticipation; orange-white forge flash hides her then reveals her already striking the next construct; camera keeps physical follow. **No transit smear, no whip pan, no motion blur.**

这是整条提示词里技术含量最高的一句：它给"瞬移"指定了一个**物理上的理由**（火光遮住 → 再出现时已经在打下一个），同时禁掉三种最常见的糊法。

### 7. 禁掉不该出现的东西

> **No dialogue or subtitles.**

字幕和台词是 AI 视频最容易自作主张加进来的东西。

### 8. 把声音也写成清单

> Furnace roar, 5 quench-impact accents, rock collapses, flash cracks, industrial percussion sting.

不是"加点氛围音"，而是**逐项点名**。而且数量要对上第 3 段——5 个熔岩造物，就是 5 次冲击音。

---

## 二、风格描述型：7 个零件，没有一个字给剧情

把 [Cliffside Silk Walk](../showcase/text-to-video.md) 逐段切：

> A graceful woman in a flowing champagne silk dress **walking** / along a cliffside path **at golden hour** / **fabric catching wind** / **warm rim light** on skin and hair / **slow lateral tracking shot, 85mm look, shallow depth of field** / refined **beauty commercial** / **photoreal, subtle film grain**

| 零件 | 这一条里是什么 |
|---|---|
| 主体 + 动作 | A graceful woman in a flowing champagne silk dress walking |
| 环境 + 时间 | along a cliffside path at golden hour |
| 材质怎么动 | fabric catching wind |
| 光 | warm rim light on skin and hair |
| 运镜 + 光学 | slow lateral tracking shot, 85mm look, shallow depth of field |
| 商业调性 | refined beauty commercial |
| 收口 | photoreal, subtle film grain |

产品类同理（Lumière Perfume Orbit，26 词）：

> Luxury perfume bottle on black glass / slow orbit / prism light splitting into soft spectral highlights / ultra-clean reflections / macro commercial beauty / razor-sharp label readable / elegant negative space

**这两个例子把预算全放在"光怎么打、镜头多长焦、材质什么手感"上，一个动作编排的字都没有。**

---

## 三、文生图：18–23 词，6 条全部含 "beauty"

6 条文生图提示词长度都在 18–23 词。它们有一个很统一的特征：**每条都自带一个"这属于哪类商业摄影"的定语，而且都落在 beauty 系**。

| 提示词 | 类型定语 |
|---|---|
| Raincoat Soft Neon | Beauty portrait |
| Tea Light Hands | wabi-sabi beauty |
| Cliffside Linen Look | airy summer beauty campaign |
| Mirror Light Study | Artistic beauty study |
| Pearl Ear Macro | jewelry beauty advertising |
| Garden House Morning | lifestyle beauty photography |

配方可以写成：

```
[画面类型] + [主体] + [环境/背景] + [光] + [材质/细节] + [商业类型定语] + [情绪]
```

两个反复出现的元素值得单独记：

- **光写了 5 条**：`soft neon bokeh`、`warm side light`、`sunlit`、`soft window light`、`morning light`
- **材质词写了 4 条**：`porcelain skin`、`linen and wood textures`、`ivory linen`、`ultra-clean reflections`

文生图的差距基本就落在"光怎么虚"和"表面什么手感"上。

---

## 四、可以直接抄的骨架

**要一段戏**，用这个填：

```text
Photoreal live-action [题材], crisp high-resolution cinema detail, clean HDR contrast,
one [焦段] lens and one uninterrupted controlled [运镜] shot.

The [主角] is a [年龄/体型/地域], [发型], [服装], [手里拿什么].
Keep one identical [主角] throughout.

Exactly [N] distinct [对手/物件] appear; [第 N 个] is [最强的那个].
Never reuse a [对手/物件]. Every [动作] hits exactly one target.
Show [N] separate contacts. No multi-target [动作].

Rotate [动作1], [动作2], [动作3], [动作4], and final [收尾动作].

Every relocation: [转场理由]; camera keeps physical follow.
No transit smear, no whip pan, no motion blur.

No dialogue or subtitles. [声音清单，逐项点名].
```

**要一张会动的画**，用这个：

```text
[主体 + 动作] + [环境 + 时间] + [材质怎么动] + [光] +
[运镜 + 焦段 + 景深] + [商业调性] + photoreal / 质感词
```

**要一张图**，用这个：

```text
[画面类型] of [主体], [环境], [光], [材质细节], [xx beauty 定语], [情绪]
```

---

## 五、三条从数据里看出来的经验

1. **词数不是越长越好，是"要不要一段戏"。** 189 词和 26 词在同一个 showcase 里并列，都能出片。
2. **否定句的密度决定稳定性。** 四条长提示词每一条都**恰好 4 处否定**（3 个 `No …` + 1 个 `Never …`），一处不多一处不少。
3. **数量和顺序必须显式写。** `Exactly 5`、`construct 5 is`、`Rotate A, B, C` —— 模型不会自己安排节奏。

---

[文生视频提示词原文](../showcase/text-to-video.md) · [文生图提示词原文](../showcase/text-to-image.md) · [回到首页](../README.md)
