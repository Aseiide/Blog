---
title: "ブログ用のリポジトリにCIでtextlintとreviewdogを導入した"
date: 2022-04-19T23:02:40+09:00
draft: false
categories:
- 技術
tags:
- CI
- GiHub Actions
---

このブログを書くのにHugo + Netlifyで運営をしているのですが、CIの勉強も兼ねてGitHub Actionsを使ってPRが作られた時点でtextlintを実行し、reviewdogでルールに違反しているところにコメントを入れるようにしてみました。
**コピペしたら動いちゃった、というあまりよろしくない感じなので正確性は保証しておりません。**

# 導入の手順

基本的には、[GitHub ActionsでZennブログの校正を自動化してみた](https://zenn.dev/yuta28/articles/blog-lint-ci-reviewdog)を参考にして入れていきました。

- SmartHRが公開しているtextlintのプリセットをプロジェクトにインストール
  - `npm install npm install textlint-rule-preset-smarthr --save-dev`
  - `textlintrc`, `package.json`, `package.lock.json`が作られる

- GitHub Actionsで使うためのファイルを`.github/workflows/reviewdog.yml`に定義する

```yml
name: reviewdog
on: [pull_request]
jobs:
  textlint:
    name: runner / textlint
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true
      - name: textlint-github-pr-review
        uses: tsuyoshicho/action-textlint@v3
        with:
          github_token: ${{ secrets.github_token }}
          reporter: github-pr-review
          level: warning
          textlint_flags: "./content/blog/*/index.md" #<-自分のディレクトリ構成に合わせる
```

- いつもの通り、PRを作る

# 導入したツールについて(メモ)

## textlint

[textlint/textlint: The pluggable natural language linter for text and markdown.](https://github.com/textlint/textlint)は文章の校正をしてくれるツール。
いろいろなプリセットがあり、日本語の技術文書プリセットなんかもある。
[よりよい文書を書くための校正ツール「textlint」のSmartHR用ルールプリセットを公開しました！｜SmartHRオープン社内報｜株式会社SmartHR](https://shanaiho.smarthr.co.jp/n/n881866630eda)こんなのが公開されていてリポジトリではこれを使っています。

## CIとは?

[GitHubの新機能「GitHub Actions」で試すCI/CD | さくらのナレッジ](https://knowledge.sakura.ad.jp/23478/)
CI、継続的インテグレーションと言われてるやつだが、実際のところよくわかっていない。
フィヨルドのチーム開発にも導入されている。
自分の感覚では、コードをpushすると、テストとかリンターとかが自動で走ってくれるやつ、という認識です。

> CIはソフトウェアのビルドやテストを自動化して頻繁に実行することでソフトウェアの品質向上や開発効率化を目指す手法

## reviewdog

reviewdogを使うことで、textlintの指摘をプルリクエストのコメントに入れてくれるらしいです。
[GitHub Actionsにreviewdogを飼ってみた！(eslint編) | DevelopersIO](https://dev.classmethod.jp/articles/shuntaka-github-actions-reviewdog/)

## npm install の --savedevって何?

# 参考

- [GitHub ActionsでZennブログの校正を自動化してみた](https://zenn.dev/yuta28/articles/blog-lint-ci-reviewdog#textlint)
