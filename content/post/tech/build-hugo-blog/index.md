---
title: "C#erが静的サイトジェネレーターHugoでブログを作ってみた"
description: "完全無料＆爆速！HugoとStackテーマで作る、画像メインの技術ブログ構築ログ"
date: 2025-12-20T16:18:10+09:00
image: cover.jpg   # ← 記事フォルダ内に cover.jpg を入れると表紙になります
categories:
    - Tech         # ← これを入れるとメニューの「Tech」に表示されます
tags:
    - Hugo
    - Blog
    - GitHub
draft: false       # ← ここを false に変更！
---

AIイラストの生成やC#でのツール開発を行っていると、どうしても **「画像がきれいに見える場所」や「コードが見やすい場所」** が欲しくなります。

既存のブログサービスも良いですが、エンジニアとしては　**「自分の手で管理できる」「Gitでバージョン管理したい」「Markdownで書きたい」**　という欲求には抗えません。

そこで今回、静的サイトジェネレーターの Hugo と、ホスティングサービスの GitHub Pages を組み合わせて、完全無料かつ爆速なブログを構築しました。 構築中にいくつか躓いたポイント（GA4の設定やGiscusなど）もあったので、備忘録として残しておきます。

なぜ Hugo + GitHub Pages なのか？
爆速: データベースを使わず、事前にHTMLを生成するため表示が一瞬です。

無料: サーバー代がかかりません。ドメイン代も（GitHubドメインなら）不要です。

画像に強い: 今回採用したテーマ「Stack」はカード型デザインで、AIイラストのギャラリーに最適でした。

管理が楽: 記事はMarkdownファイル。GitでPushするだけで公開されます。

使用した技術スタック
Engine: Hugo (Extended版)

Theme: Stack

Hosting: GitHub Pages

Comments: Giscus (GitHub Discussions利用)

Analytics: Google Analytics 4 (GA4)

# 1. 環境構築とテーマの導入
まずはHugoのインストールから。Stackテーマを使うには extended バージョンが必須です。

```Bash
# バージョン確認（extendedと出ればOK）
hugo version
# hugo v0.128.0-......+extended
```

サイトを作成し、テーマをサブモジュールとして追加します。

```Bash
hugo new site my-blog --format yaml
cd my-blog
git init
git submodule add https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack
```

# 2. こだわりの設定 (hugo.yaml)
今回一番工夫したのは、AIアートブログならではの 「カテゴリ設計」 です。 通常のカテゴリ・タグに加えて、models（使用モデル）や lora を設定ファイル（hugo.yaml）で定義しました。

```YAML
# --- AIブログ用カテゴリ設定 ---
taxonomies:
  category: categories
  tag: tags
  model: models       # Checkpoint (例: PonyV6)
  lora: loras         # LoRA (例: FlatLora)
```

これで、記事のヘッダーに models: ["JANKU V6"] と書くだけで、モデルごとの一覧ページが自動生成されるようになります。データベースいらずでこれは便利すぎます。

# 3. 躓いたポイント：GA4の設定
Google Analytics 4の設定で少しハマりました。 hugo.yaml は大文字と小文字を厳密に区別するため、以下のように書く必要がありました。

```YAML
# ❌ 間違い（これだとタグが出力されない）
services:
  googleAnalytics:
    ID: "G-XXXXXXXXXX"

# ✅ 正解（idは小文字！）
services:
  googleAnalytics:
    id: "G-XXXXXXXXXX"
```

テーマのドキュメントやHugoの仕様をよく確認することが大事ですね。

# 4. コメント欄の実装 (Giscus)
静的サイトにはデータベースがないため、コメント欄の実装が課題になります。 今回は Giscus を採用しました。これは GitHub Discussions の機能を利用してコメント欄を実現するツールです。

完全無料

GitHubアカウントで書き込める（エンジニア・開発者向けに最適）

スパムが来にくい

導入は、Giscusアプリをリポジトリにインストールし、発行された repoId と categoryId を設定ファイルに貼るだけでした。

# 5. 公開 (GitHub Actions)
GitHub Pagesへのデプロイは、GitHub Actions を使って自動化しています。 ローカルで記事を書いて git push すると、GitHub上のサーバーが勝手にHugoをビルドして公開してくれます。

hugo.yaml (Workflow用) を .github/workflows/ に配置するだけで動くので、CI/CDの知識が深くなくても大丈夫でした。

# まとめ：これからの運用
セットアップは完了し、プライバシーポリシーやお問い合わせフォームなど、収益化（AdSense等）を見据えた基盤も整いました。

これからは、メインである 「AIイラストの検証」 や 「C#ツールの開発ログ」 をどんどん発信していこうと思います。 「間口は広く、奥行きは深く」をモットーに運営していきますので、よろしくお願いします！