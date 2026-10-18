# 提示词积木：从 12 条真实提示词里拆出来的可复用片段

不要从零写 200 词。把下面的积木按需拼起来，比背整条模板快得多。

每条积木都标了**出处**——引号里是原文，不是改写。

---

## 一、开场：定画质和镜头

| 积木 | 原文（节选） | 作用 |
|---|---|---|
| **写实 + 画质** | "Photoreal live-action …" + "crisp high-resolution cinema detail" + "clean HDR contrast" | 三个词压住"AI 塑料感" |
| **一镜到底** | "one wide lens and one uninterrupted controlled handheld pursuit shot" | 从根上禁止模型自己切镜头 |
| **焦段 + 跟拍** | "one 40mm-equivalent lens and one uninterrupted controlled handheld tracking shot along the train roof" | 指定焦段=指定透视，跟拍=指定运动方式 |

出处：Volcano Forge Escape（shots 1–2）、Maglev Train Duel（shot 2）。

> **最关键的是 `one uninterrupted … shot`。** 不写这句，模型会给你七八个碎镜头拼起来的东西。

---

## 二、锁住主角

| 积木 | 原文（节选） | 作用 |
|---|---|---|
| **外形清单** | "a muscular North African woman, late 20s, shaved sides with dense curls, glowing ember freckles, soot-streaked bronze armor over ash linen, one living molten hammer in her right hand" | 年龄 + 体型 + 发型 + 服装 + 手持物，五项给全 |
| **身份锁** | "Keep one identical smith-mage throughout." | 一句话防换脸 |

出处：Volcano Forge Escape。

**没有 `Keep one identical X throughout` 这句，第 3 秒就会变成另一个人。**

---

## 三、给数量，给终点

| 积木 | 原文 | 作用 |
|---|---|---|
| **精确数量** | "Exactly 5 distinct lava constructs emerge" | 数字限定，避免无限平铺 |
| **指定最后一个** | "construct 5 is a towering slag titan with a chain-anvil" | 给视频一个高潮点 |

出处：Volcano Forge Escape。

---

## 四、否定积木（最容易被忽略，也最有用）

| 积木 | 原文 | 堵住什么 |
|---|---|---|
| **不许复用** | "Never reuse a construct." | 五个镜头长得一模一样 |
| **一次只打一个** | "Every hammer blow hits exactly one target. … No multi-target smash." | 模型"一锤打一片"的偷懒 |
| **不许糊** | "No transit smear, no whip pan, no motion blur." | 转场糊成一团 |
| **不许加字幕** | "No dialogue or subtitles." | 自作主张加台词和字幕 |

出处：Volcano Forge Escape。

> 四条长提示词，**每条都恰好 4 处否定**（3 个 `No` + 1 个 `Never`）。这不是巧合，是配比。

---

## 五、动作轮换

| 积木 | 原文 | 作用 |
|---|---|---|
| **动作清单** | "Rotate overhead forge strike, lateral quench-smash, vault over magma rivulet, ground-spike kick, and final titan knee break." | 五个动作写成一个列表，否则五个镜头一个样 |

出处：Volcano Forge Escape。

---

## 六、转场规则

| 积木 | 原文 | 作用 |
|---|---|---|
| **给瞬移一个物理理由** | "Every relocation: micro-anticipation; orange-white forge flash hides her then reveals her already striking the next construct; camera keeps physical follow." | 用画面元素遮住 → 再出现，比"瞬移"自然 |

出处：Volcano Forge Escape。

---

## 七、声音清单

| 积木 | 原文 | 作用 |
|---|---|---|
| **逐项点名** | "Furnace roar, 5 quench-impact accents, rock collapses, flash cracks, industrial percussion sting." | 不是"加点氛围音"，是给每个动作配一个音 |

出处：Volcano Forge Escape。注意 **`5 quench-impact accents` 要和第三段的"Exactly 5"对上**。

---

## 八、把积木拼起来

```text
Photoreal live-action [题材], crisp high-resolution cinema detail, clean HDR contrast,
one [焦段] lens and one uninterrupted controlled [运镜] shot.

The [主角] is a [年龄/体型/地域], [发型], [服装], [手持物].
Keep one identical [主角] throughout.

Exactly [N] distinct [对手/物件] appear; [第 N 个] is [最强的那个].
Never reuse a [对手/物件]. Every [动作] hits exactly one target. No multi-target [动作].

Rotate [动作1], [动作2], [动作3], [动作4], and final [收尾动作].

Every relocation: [遮住它的东西] hides her, then reveals her already [下一个动作];
camera keeps physical follow. No transit smear, no whip pan, no motion blur.

No dialogue or subtitles. [声音 1], [N] 次 [声音 2], [声音 3].
```

---

## 九、四个常见错误

1. **只写主体，不写镜头** —— 结果是一堆不知从哪来的碎镜头
2. **写了数量，没写"最后一个是谁"** —— 视频没有高潮，十几秒里一路平铺过去
3. **一条否定都不写** —— 模型会挑最省力的方式糊过去
4. **声音写"加一些氛围音"** —— 应该逐项点名，而且数量要和对白/动作对上

---

[文生视频原文](../showcase/text-to-video.md) · [写法拆解](prompt-patterns.md) · [回到首页](../README.md)
