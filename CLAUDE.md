# CLAUDE.md

このファイルは、このリポジトリで作業する際に Claude Code が参照するガイドです。

## リポジトリ概要

- **m9logs** … 「キッド」による雑多な趣味ブログ。
- Jekyll で構築した静的サイトで、GitHub Pages（GitHub Actions 経由）で公開している。
- 公開 URL: https://m9logs.net （`CNAME` で独自ドメインを設定）
- 主な話題: ギター、歌、ゲーム、アニメ、釣り、キャンプ、バイク、カメラ、登山など。

## 技術スタック

- Jekyll 4.1（`Gemfile` で指定）
- テーマ: `minima` 2.5（一部を `_includes` / `_sass` で上書き）
- プラグイン: `jekyll-feed`, `jekyll-auto-image`
- Markdown: kramdown（`hard_wrap: true`）
- タイムゾーン: `Asia/Tokyo`

## ディレクトリ構成

- `_posts/` … 公開記事（Markdown）。約100本以上。
- `_draft/` … 下書き。日付は `2099-...` にして本番ビルドに含まれないようにしている。
- `_includes/` … テーマ上書き用の部分テンプレート（`head.html`, `post_list.html`）。
- `_sass/` … Sass パーシャル（`base.scss`）。
- `assets/` … 画像などの静的ファイル。`assets/<年>/<月>/` の階層で管理。
- `docs/` … （`exclude` 対象。ビルドには含まれない）
- `index.md` / `categories.md` / `all_posts.md` / `kidhub.md` / `404.html` … 各ページ。
- `_config.yml` … サイト設定。
- `.github/workflows/jekyll.yml` … GitHub Pages へのデプロイ用ワークフロー。
- `_site/` … ビルド成果物（gitignore 済み。編集しない）。

## 記事（投稿）のルール

### ファイル名

`_posts/YYYY-MM-DD-<slug>.md` の形式。

### Front Matter

既存記事に合わせて以下の形式で記述する。

```yaml
---
layout: post
title: 記事タイトル
date: 2025-03-16 12:00:00 +0900
author: キッド
comments: true
categories:
- fishing
---
```

- `date` は `+0900`（JST）を付ける。
- `categories` は原則リスト形式（`- xxx`）で記述する。1件のみのインライン形式（`categories: game`）の記事も一部あるが、新規作成時はリスト形式に統一するのが望ましい。
- パーマリンク: `/posts/:year-:month-:day-:title/`（`_config.yml` で設定）。

### 既存カテゴリ

`camp`, `game`, `diary`, `fishing`, `music`, `movie`, `photo`, `m9oftheyear`, `venezia`, `travel`, `mountain`, `anime`, `development`, `motor`, `book`, `astronomy`, `gadget`, `car`, `birdwatching`, `art` など。新規記事はできるだけ既存カテゴリを再利用する。

### 画像

- `assets/<年>/<月>/` に配置する（例: `assets/2025/03/20250316_pond.jpg`）。
- 記事本文からは絶対パスの `<img>` タグで参照する（例: `<img src="/assets/2025/03/20250316_pond.jpg" alt="">`）。

### 下書き

- 執筆中の記事は `_draft/` に置き、日付を `2099-...` にしておく（本番ビルドには含まれない）。
- 公開時に `_posts/` へ移動し、日付・ファイル名を正しい公開日に変更する。

## ローカルでの動作確認

Docker Compose で起動する（ポート `3000` で閲覧、livereload あり）。

```
docker compose up
```

または Ruby 環境が整っている場合:

```
bundle exec jekyll serve
```

## デプロイ

- `master` ブランチへ push すると `.github/workflows/jekyll.yml` が動き、GitHub Pages へ自動デプロイされる。
- 手動実行（workflow_dispatch）も可能。

## 注意事項

- `_site/` はビルド成果物なので直接編集しない。
- テーマ（minima）の挙動を変えたい場合は、`_includes/` や `_sass/` に該当ファイルを置いて上書きする。
