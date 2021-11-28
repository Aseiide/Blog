---
title: "データベース設計について学んだ事"
date: 2021-07-22
draft: false
categories:
  - 雑記
tags:
  - FJORDBOOTCAMP
---
# # データベース設計ふりかえり
ブートキャンプのデータベース設計の課題でかなり時間がかかったので振り返りとして記録しておこうと思います。  
**※フィヨルドブートキャンプ受講生の方はネタバレ注意**

# 課題の内容
Twitterの主な機能をもとにER図を作成するという内容

```md
対象の機能
- ユーザを表示する
- ツイートする
- ツイートに返信する
- リツイートする(引用リツイートも)
- フォローする
- フォロー一覧を表示する
- フォロワー一覧を表示する
- リストにユーザーを追加する
- リスト一覧を表示する
```

# 最初の提出物と最終の提出物

## 最初の提出物

ざっと資料を読んで適当に作ったER図
![image1](/images/database/database1.png)


## 最終の提出物

<details>

![image2](/images/database/database2.png)

</details>

# 学んだ事
## リプライについて

- 1個のツイートに対して複数のリプライがあるという関係
- リプライもすべて「ツイート」
- Repliesテーブルに切り出し、FKとしてtweet_idをもたせる事にしました


![image3](/images/database/database3.png)



## RT/引用RTについて

- RTも引用RTもまた「ツイート」
- フラグを導入して判別
- フラグが0のときRTされていない、グラグが1の時、RTされている
![image4](/images/database/database4.png)


## フォロー/フォロワーの関係

- 自己参照している
- Relationshipという中間テーブル
![image5](/images/database/database5.png)

## ユーザーとリストの関係

- ユーザーはリストを複数持っている
- リストはユーザーを複数持っている
- 多対多の関係になっている
- Users_Listsという中間テーブルを作って1対多の関係になるようにする
![image6](/images/database/database6.png)

# 参考
- [達人に学ぶDB設計 徹底指南書](https://www.amazon.co.jp/%E9%81%94%E4%BA%BA%E3%81%AB%E5%AD%A6%E3%81%B6DB%E8%A8%AD%E8%A8%88-%E5%BE%B9%E5%BA%95%E6%8C%87%E5%8D%97%E6%9B%B8-%E5%88%9D%E7%B4%9A%E8%80%85%E3%81%A7%E7%B5%82%E3%82%8F%E3%82%8A%E3%81%9F%E3%81%8F%E3%81%AA%E3%81%84%E3%81%82%E3%81%AA%E3%81%9F%E3%81%B8-%E3%83%9F%E3%83%83%E3%82%AF/dp/4798124702/ref=sr_1_1?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&dchild=1&keywords=%E9%81%94%E4%BA%BA%E3%81%AB%E5%AD%A6%E3%81%B6&qid=1626932862&sr=8-1)
- [楽々ERDレッスン](https://www.amazon.co.jp/%E6%A5%BD%E3%80%85ERD%E3%83%AC%E3%83%83%E3%82%B9%E3%83%B3-CodeZine-BOOKS-%E3%82%B9%E3%82%BF%E3%83%BC%E3%83%AD%E3%82%B8%E3%83%83%E3%82%AF-%E7%BE%BD%E7%94%9F/dp/4798110663/ref=sr_1_1?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&dchild=1&keywords=ERD%E3%83%AC%E3%83%83%E3%82%B9%E3%83%B3&qid=1626932904&sr=8-1)
- [フラグについて](https://qiita.com/wanko5296/items/f1af9c7bf020e867c2dd)
