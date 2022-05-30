---
title: "自作Railsアプリケーション「ROASTERS MAP」"
date: 2021-04-27
draft: false
summary: '現在地付近のコーヒーショップをマップで確認できるアプリケーション'
---

# ROASTERS MAP とは

![スクリーンショット 2021-04-28 19 07 26](https://user-images.githubusercontent.com/45246171/116386709-0127bc80-a855-11eb-8387-303592fda1cb.png)

[アプリはこちらから使うことが出来ます](https://aqueous-hollows-28552.herokuapp.com/)

ROASTERS MAP は、近くの自家焙煎のコーヒーショップをマップ上で見ることができるアプリケーションです。

# 使用している技術とAPI

- Ruby 2.7.2
- Ruby on Rails 6.0.3.6
- Bootstrap
- RSpec
- [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript/overview)
- [Geocoding API](https://developers.google.com/maps/documentation/geocoding/overview)
- Heroku

# 使用方法

1. 使っているブラウザに位置情報の権限を渡してください

- Mac をお使いの場合
  システム環境設定 > セキュリティとプライバシー > 位置情報サービス > 使っているブラウザにチェックを入れる

2. 現在地を取得して近くのコーヒーショップを表示します
   なお、現在は東京都と福岡市を中心に表示しています

# 今後実装予定の機能

- 管理者ログインの実装
- ピンをクリックしたら店名などの情報が表示される

# 実装の解説
実装についての詳細な解説は[こちら](https://qiita.com/Aseiide/items/36fa33b1dbd97a571814)に記載しました。
