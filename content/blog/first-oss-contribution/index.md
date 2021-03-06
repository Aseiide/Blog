---
title: "初めてのOSSコントリビュート"
date: 2021-11-13T23:39:21+09:00
draft: false
summary: 'OSSにプルリクエストを出してマージされたときの記録'
categories:
  -  技術
tags:
  -   OSS
---

OSSにプルリクエストを出して初めてマージされたのでその時の事を記録として残しておこうと思います。  
2021年内の目標にしていたので目標を一つ達成できました。

# マージされたプルリクエスト

<https://github.com/voxpupuli/puppet-elasticsearch/pull/1131>

Rubyの`good fisrst issue`を探しているときにたまたま見つけたのでサッとtypoを修正したのを出したらあっさりとマージされました。  

# 余談: なぜOSSにプルリクエストを送ろうと思ったか

理由は2つあって、「単純に興味があったから」と「Rubyコミュニティの周りを見ていて自分もやりたい！と思ったから」です。  
OSSのなんたるか、とかは全然わかっていないのですが、少なくともプログラミングの学習をしている身としてOSSの恩恵を受けているなーとは日々感じているところです。  
普段参加しているRubyコミュニティにOSSにコントリビュートしてる方が多くて、その方々を見ていて自分もやってみたいと思っていました。  

# issue発見からプルリクエストを送るまでの過程

個人的に2021年の目標として「OSSにコントリビュートする」を掲げていて、時間があるときには`good first issue`を漁るようにしていました。  
プルリクエストを送るまでの詳細なやり方はネットに記事が落ちているので、ここでは超初心者の過程を簡単に残しておきます。  

1.  [gooddirstissue.dev](https://goodfirstissue.dev/)でissueを見つける  
2.  対象リポジトリで概要を把握し、`CONTRIBUTE.md`などのコントリビュートに関するドキュメントを読む。  
forkする場合が多いと思いますが、コントリビュートするときの注意事項とかやりかたが書かれている。
3.  リポジトリをfork
4.  forkしたリポジトリをローカルにcloneする
5.  ブランチを切って、修正してpushする。今回は対象ファイルのtypoを直しました。
6.  本家に向けてプルリクエストを送る。

このような感じでやっていきました。マージされるかはわからないので、最初のうちは「マージされたらラッキー」くらいのメンタルがいいかもしれません。  

# 次回に向けて(反省)

継続的にやっていきたいので反省というか改善点も挙げておきます。

-   まったく馴染みの無いリポジトリだったこと
    -   プルリクエストを出すとき、本来はテストをパスさせる必要があったのですがリポジトリ自体の使い方が分からず手元でテストを通せないままの提出となってしまいました。
-   技術的な修正ではなくtypoだったことが悔しい
    -   今回は、たまたま`goodfirstissue.dev`で見つけたものでリポジトリ自体は使ったことがありませんでした。次回以降は自分の馴染みのあるものでできるようにしたいと考えています。

# ひとこと

まず、個人の目標を達成できたことがすごく嬉しいです。  
OSSコントリビュートの一歩を踏み出すことができたので、より貢献できるように学習を進めて技術的な修正も送れるようにしたいと考えています。  

# 参考リンク

-   [gooddirstissue.dev](https://goodfirstissue.dev/)
-   [はじめてのOSSコントリビュート](https://qiita.com/Yuichi_Yogo/items/81bd00880a02fd5e816c)
