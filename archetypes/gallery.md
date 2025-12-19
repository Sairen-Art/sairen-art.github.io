---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
image: "cover.webp"
categories:
    - Gallery
tags:
    - Original
models:
    - PonyDiffusionV6
loras:
    - 
description: "ここに作品のキャプションや一言コメントを書きます。"
---

### Prompt
```text
(masterpiece, best quality), ...
```
```
### Workflow / Comment
ここにComfyUIの構成や、苦労した点などを書きます。


---

### 次のアクション：記事を作ってみましょう

テンプレートが直ったので、実際に記事ファイルを生成して、画像を置いてみましょう。

1.  **記事の生成:**
    ```powershell
    hugo new content/post/gallery/first-art --kind gallery
    ```

2.  **画像の配置:**
    * 作成されたフォルダ: `content/post/gallery/first-art/`
    * この中に、表示したい画像を **`cover.webp`** （または `cover.jpg` 等）という名前で保存してください。
    * ※もし画像が `.jpg` なら、記事ファイル（`index.md`）内の `image: "cover.webp"` を `image: "cover.jpg"` に書き換えてください。

3.  **確認:**
    `hugo server` でブラウザを確認し、画像付きで記事が表示されれば成功です！