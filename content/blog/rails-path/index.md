---
title: "Railsのパスの書式について学んだこと"
date: 2021-10-29T17:57:00+09:00
draft: false
summary: 'Railsのルーティングにおいて_pathと_urlをどう使い分けるか'
categories:
  - 技術
tags:
  - Rails
  - 技術メモ
---

# pathの書式`_url`と`_path`をどうやって使い分けるか

pathの書式について`_url`と`_path`の２種類があるのはわかっていたが、なんとなくよく見るからという理由だけで`_path`を使っていた。  
調べると使い分けがあるらしい。  

## 結論

- リダイレクトする場合は、`_url`を使う
- それ以外の場合は、`_path`を使う

## なぜ？

- `_url`の場合、完全なURLの文字列を返す。HTTPの標準としてはリダイレクトのときに完全なURLが要求されるから。  
- `_path`はルート文字列以下を返す  

繰り返しだが、HTTPの標準としてリダイレクトの際は完全なURLの方がいいので、`_url`を使う。それ以外はRails Wayに沿って`_path`と書く。  

# 参考
[Railsチュートリアル](https://railstutorial.jp/chapters/filling_in_the_layout?version=6.0#sec-rails_routes)
