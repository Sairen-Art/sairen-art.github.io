---
title: "PonyDiffusion V6 とOneObsessionの比較検証"
date: 2025-12-16T13:46:55+09:00
image: "cover.webp"
categories:
    - Gallery
    - Review
tags:
    - JANKU V6
    - One obsession V19
    - Original
models:
    - JANKU V6
    - One obsession V19
description: "JANKU V6とOne obsession V19の比較検証を行いました。"
---

## 比較検証 (Slider)

ベースモデルと、oneObsessionの比較です。
スライダーを動かすと、

{{< slider 
    before="base.webp" 
    after="after.webp" 
    label_before="Base Model (JANKU V6)" 
    label_after="One obsession V19" 
>}}

JANKU V6とOne obsession V19の描写を比較すると、その方向性の違いが明確に現れます。JANKU V6は輪郭線が際立つアニメ調の表現を得意とし、キャラクターを鮮やかに描き出します。一方、One obsession V19は質感や陰影が非常に緻密で、実写に近いリアルな空気感を纏っています。スライダーを動かして、それぞれのモデルが持つ独特の質感の差をぜひ体感してみてください。

個人的にはJANKの方が好みです。

---

## 制作ノート

今回は **KritaAIDiffusion** を使用して生成しました。

---

## Generation Data

<details>
<summary><strong>クリックしてプロンプトと設定を表示</strong></summary>

<br>

| 項目 | 設定値 |
|---|---|
| Model | JANKU V6 |
| Sampler | Euler a |
| Steps | 28 |
| CFG Scale | 7.0 |
| Seed | 123456789 |
| Clip Skip | 2 |

#### Prompt
```text
1girl, breasts, solo, jewelry, large breasts, covered navel, nun, mole, cross, brown hair, earrings, one eye closed, blue eyes, necklace, cleavage, long hair, dress, piercing, looking at viewer, black dress, parted lips, ear piercing, arms up, habit, mole on breast, indoors, church, temple, arms behind head, cross necklace, blunt bangs, cross earrings, long sleeves, mole under eye, clothing cutout, (masterpiece, high quality, best quality:1.2), newest, absurdres, amazing quality, absurdly detailed composition, very aesthetic, extremely detailed, very awa, hyperdetailed,
IllusP0s,  usnr dynamic pose, foreshortening, extreme perspective masterpiece, best quality, very aesthetic , lazypos,masterpiece, best quality, very aesthetic, ultra-detailed, photorealistic, semi-realistic, highly detailed skin and texture, absurdres, newest, 8K,Mid4Mb, konya karasue, (shimhaq:0.6), (k-suwabe:0.70), abstract background, soft shading, Semi-realism, usnr
```

####  NegativePrompt
```text
(bad quality:1.1),(worst quality:1.1),bad details, (bad hands:1.2), sketch, jpeg artifacts, signature, watermark, ugly, poorly drawn, blurry, ugly, bad face, loli, (sweat:1.3), (wet:1.3), (oil:1.3), (shiny skin:1.3), (wet fur:1.5), water drops, glossy finish, plastic skin,, bad quality, low resolution, blurry,(stiff expression:1.5), (expressionless:1.5)
```

