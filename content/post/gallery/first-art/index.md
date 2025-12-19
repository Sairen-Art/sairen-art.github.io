---
title: "PonyDiffusion V6 と自作LoRAの比較検証"
date: 2025-12-16T13:46:55+09:00
image: "cover.webp"
categories:
    - Gallery
    - Review
tags:
    - PonyDiffusion
    - LoRA
    - Original
models:
    - PonyDiffusionV6 XL
loras:
    - "MyStyle_LoRA_v1: 0.8"
description: "PonyDiffusion V6をベースに、自作した画風LoRA（強度0.8）の適用テストを行いました。色使いと線の太さの変化に注目しています。"
---

## 比較検証 (Slider)

ベースモデルと、LoRA適用後（Weight: 0.8）の比較です。
スライダーを動かすと、LoRAによって彩度が上がり、主線がくっきりする様子が確認できます。

{{< slider 
    before="base.webp" 
    after="lora.webp" 
    label_before="Base Model (Pony V6)" 
    label_after="With LoRA (0.8)" 
>}}

---

## 制作ノート

今回は **ComfyUI** を使用して生成しました。
Pony系モデルはプロンプトの効きが良いですが、特定の画風を定着させるためにLoRAを作成しました。

### 苦労した点
* LoRAの学習データセット作成時に、タグ付け（キャプション）で背景情報を除外しないと、キャラクターの色味まで変わってしまう現象に苦戦しました。
* C#の自作ツールで「背景タグを一括削除」する機能を作り、データセットを再構築したところ改善しました。

---

## Generation Data

<details>
<summary><strong>クリックしてプロンプトと設定を表示</strong></summary>

<br>

| 項目 | 設定値 |
|---|---|
| Model | PonyDiffusionV6 XL |
| Sampler | Euler a |
| Steps | 28 |
| CFG Scale | 7.0 |
| Seed | 123456789 |
| Clip Skip | 2 |

#### Prompt
```text
(masterpiece, best quality, score_9, score_8_up, score_7_up),
1girl, solo, standing, looking at viewer, simple background, white background,
silver hair, long hair, blue eyes, school uniform, serafuku,
<lora:MyStyle_LoRA_v1:0.8>
```

####  NegativePrompt
```text
(low quality, worst quality:1.4), (bad anatomy), (inaccurate limb),
bad hands, text, error, missing fingers, extra digit, fewer digits,
cropped, jpeg artifacts, signature, watermark, username, blurry,
score_4, score_5, score_6
```

