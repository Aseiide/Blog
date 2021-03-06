---
title: "自作LINE BOT「アヤセ教えて君」"
date: 2020-09-10
draft: false
summary: '電車の時刻を通知してくれるLINE BOT'
---

# アヤセ教えて君とは
アヤセ教えて君は、東京メトロ千代田線の「綾瀬行」電車の時刻を返すLINE BOTです。  
ユーザーが現在いる駅を送信すると、電車の時刻が返ります。

# GitHub

[ayase_bot/README.md at master · Aseiide/ayase_bot](https://github.com/Aseiide/ayase_bot/blob/master/README.md)

# デモ
![demo](https://user-images.githubusercontent.com/45246171/92308552-66ceec00-efd9-11ea-93bd-a757e122a5ac.gif)

# 使用している技術
- Ruby 2.6.6
- Messaging API
- 駅すぱあとWebサービス（フリープラン）
- Heroku

# 技術スタック
![ayasebot-sequence](https://user-images.githubusercontent.com/45246171/92366693-757be700-f130-11ea-8efd-7b52c95f063d.png)

# 使っているgem
- sinatra
- line-bot-api
- nokogiri
- net/http
- net/http
- json
- uri


# 使い方
以下のコマンドでリポジトリを取得できます
```
https://github.com/Aseiide/ayase_bot
```
その後bundle install してください
```
bundle install
```
# QRコード
![ayasebot](https://user-images.githubusercontent.com/45246171/92367721-c213f200-f131-11ea-8de9-26086b4d2938.png)

安定版として公開しています。
こちらのQRコードをご利用ください。

# Qiita 技術解説

[Ruby初心者が2ヶ月で電車の時刻を教えてくれるLINE BOTを作って公開した話 - Qiita](https://qiita.com/Aseiide/items/04d1f62c9616d9aaa7b1)
