---
title: "鹿児島Ruby会議02へ行ってきました"
date: 2023-03-07T17:14:28+09:00
draft: false
summary: "鹿児島Ruby会議02参加レポート"
categories:
- rubykaigi
tags:
- RubyKaigi
- 鹿児島Ruby会議
- Rubyのしくみ
- fjordbootcamp
---
鹿児島Ruby会議02へ参加してきました。  
現役と浪人と鹿児島大学を受験したので、鹿児島は4度目くらいの訪問でした。

# 会議本編
## QUICの話 by うなすけsan
- 雑メモ
  - Rubyアソシエーションの採択プロジェクトとして取り組んでいることを知った
  - メンターは笹田さんで笹田さんと一緒に勧めている
  - pythonにあるQUICの実装をRubyに移植しており、めちゃくちゃ大変そう
  - QUICについては、[QUICをゆっくり解説 – 新しいインターネット通信規格 | IIJ Engineers Blog](https://eng-blog.iij.ad.jp/quic)が参考になりそうだったのであとで見る

以下、感想です。  
ありがたいことに図があったので10%くらい理解できた(気がする)。
TCPとかUDPとか、**「やっぱ基本情報大事」** という気持ちになりました。
デモがあって、何やってるのか雰囲気だけでもつかめたのは良かったです。

## 「初めてRailsアプリをリリースしました！」のその後 by トミーsan
- 登壇資料: [What Ever Happened to Baby Rails App? - Speaker Deck](https://speakerdeck.com/eatplaynap/what-ever-happened-to-baby-rails-app)
- 雑メモ
  - 自作サービスのその後のお話
  - フィヨルド卒業のため/就職のためのサービスなので現在も稼働しているサービスは結構少ない
  - リリースしてからのリアルな心境と今の心境がうまく表現されていた
  - 自作サービスを自分の技術の実験場にする
  - 最後には、「楽しい」が原動力だったとトミーさんが気づき、**プログラミングを楽しむために自分が興味あることをやってる**と言ってたのが本当によかった。

以下、感想。  
トミーさんとはフィヨルドでの学習中、ほぼ同じペースで進めていた同期?仲間?でした。  
自分と立場が近いからか、自作サービスのお話で結局楽しいが原点だったということでした。  
自作サービスがバズったことを「過去の栄光」と悪い意味ではなく捉えている点も素晴らしいなと思いました。  
過去のブログでも書いた([OSSとの向き合い方を考える | a_ide_1995](https://a-ide-1995.com/blog/icare-oss-event/))けど、確かkoicさんも「楽しんでやってたら今になった」的なことを言っていたし、いろんなエンジニアとお話しても皆さん何かしら楽しんでやっているのを見ているので、**楽しいと思えるかどうか**って本当に重要なのだなと感じました。  

## mrubyでマイコンの世界に足を踏み入れる by yuuu san
- 登壇資料: [mrubyでマイコンの世界に足を踏み入れる - Speaker Deck](https://speakerdeck.com/yuuu/mrubydemaikonnoshi-jie-nizu-wota-miru-reru)

- 雑メモ
  - 福岡のときよりはもっと敷居を下げた話(のように感じました)
  - マイコンとはなにか、mrubyをどうやって実行しているかという話を聞けて遠く感じていた組み込みとかハードウェアといった技術領域を近く感じられるトークでした
  - 福岡にはmrubyに詳しい人がいるので勉強したいと思ったらいい環境だと思う
  - micropythonにかなり遅れを取っていて、今後あるべき姿とか目指す方向を聞けた


## たのしいRubyの構文解析ツアー by しおいsan
- 登壇資料: [たのしいRubyの構文解析ツアー - Speaker Deck](https://speakerdeck.com/coe401_/tanosiirubynogou-wen-jie-xi-tua)
- 雑メモ
  - Rubyの構文解析の話
  - 私もすごくRubyの言語処理系に興味があるので、小難しい話をわかりやすくスライドの落とし込んでいてすばらしかった
  - 参考資料には、[RHC](https://i.loveruby.net/ja/rhg/book/)とRubyのしくみをあげられていて、教科書的存在だと認識できた
  - RHCもRubyのしくみも途中で挫折してしまったので諦めずに何度も読もう
    - しおいさんとホワイエしてたときに「私(しおいさん)も何回も読み返しました！」と言っていたので諦めないぞ
    - しおいさんができるのだから、自分もやれる気がしている
  - はじめての質問
    - カンファレンスで初めて質問をした
    - 1. 2つ以外に参考にした資料があれば教えてほしい
    - 2. なにがきっかけでMRIに興味を持つようになったか
    - 自分で質問しといてアレなんですけど、緊張しまくってしおいさんの回答をあんま覚えてない。

### おまけ: 手元で-yオプションを実行してみた
```
$ ruby -ye '1+2'
Starting parse
Entering state 0
Reducing stack by rule 1 (line 1327):
lex_state: NONE -> BEG at line 1328
vtable_alloc:12570: 0x0000600002db0440
vtable_alloc:12571: 0x0000600002db0460
cmdarg_stack(push): 0 at line 12584
cond_stack(push): 0 at line 12585
-> $$ = nterm $@1 (1.0-1.0: )
Stack now 0
Entering state 2
Reading a token:
lex_state: BEG -> END at line 8514
lex_state: END -> END at line 7813
Next token is token "integer literal" (1.0-1.1: 1)
Shifting token "integer literal" (1.0-1.1: 1)
Entering state 41
Reducing stack by rule 642 (line 5048):
   $1 = token "integer literal" (1.0-1.1: 1)
-> $$ = nterm simple_numeric (1.0-1.1: )
Stack now 0 2
Entering state 120
Reducing stack by rule 640 (line 5037):
   $1 = nterm simple_numeric (1.0-1.1: )
-> $$ = nterm numeric (1.0-1.1: )
Stack now 0 2
Entering state 119
Reducing stack by rule 590 (line 4661):
   $1 = nterm numeric (1.0-1.1: )
-> $$ = nterm literal (1.0-1.1: )
Stack now 0 2
Entering state 106
Reducing stack by rule 307 (line 2938):
   $1 = nterm literal (1.0-1.1: )
-> $$ = nterm primary (1.0-1.1: )
Stack now 0 2
Entering state 90
Reading a token:
lex_state: END -> BEG at line 9646
Next token is token '+' (1.1-1.2: )
Reducing stack by rule 261 (line 2641):
   $1 = nterm primary (1.0-1.1: )
-> $$ = nterm arg (1.0-1.1: )
Stack now 0 2
Entering state 88
Next token is token '+' (1.1-1.2: )
Shifting token '+' (1.1-1.2: )
Entering state 370
Reading a token:
lex_state: BEG -> END at line 8514
lex_state: END -> END at line 7813
Next token is token "integer literal" (1.2-1.3: 2)
Shifting token "integer literal" (1.2-1.3: 2)
Entering state 41
Reducing stack by rule 642 (line 5048):
   $1 = token "integer literal" (1.2-1.3: 2)
-> $$ = nterm simple_numeric (1.2-1.3: )
Stack now 0 2 88 370
Entering state 120
Reducing stack by rule 640 (line 5037):
   $1 = nterm simple_numeric (1.2-1.3: )
-> $$ = nterm numeric (1.2-1.3: )
Stack now 0 2 88 370
Entering state 119
Reducing stack by rule 590 (line 4661):
   $1 = nterm numeric (1.2-1.3: )
-> $$ = nterm literal (1.2-1.3: )
Stack now 0 2 88 370
Entering state 106
Reducing stack by rule 307 (line 2938):
   $1 = nterm literal (1.2-1.3: )
-> $$ = nterm primary (1.2-1.3: )
Stack now 0 2 88 370
Entering state 90
Reading a token:
lex_state: END -> BEG at line 9365
Next token is token '\n' (1.3-1.3: )
Reducing stack by rule 261 (line 2641):
   $1 = nterm primary (1.2-1.3: )
-> $$ = nterm arg (1.2-1.3: )
Stack now 0 2 88 370
Entering state 606
Next token is token '\n' (1.3-1.3: )
Reducing stack by rule 229 (line 2480):
   $1 = nterm arg (1.0-1.1: )
   $2 = token '+' (1.1-1.2: )
   $3 = nterm arg (1.2-1.3: )
-> $$ = nterm arg (1.0-1.3: )
Stack now 0 2
Entering state 88
Next token is token '\n' (1.3-1.3: )
Reducing stack by rule 64 (line 1792):
   $1 = nterm arg (1.0-1.3: )
-> $$ = nterm expr (1.0-1.3: )
Stack now 0 2
Entering state 75
Next token is token '\n' (1.3-1.3: )
Reducing stack by rule 39 (line 1608):
   $1 = nterm expr (1.0-1.3: )
-> $$ = nterm stmt (1.0-1.3: )
Stack now 0 2
Entering state 73
Next token is token '\n' (1.3-1.3: )
Reducing stack by rule 8 (line 1386):
   $1 = nterm stmt (1.0-1.3: )
-> $$ = nterm top_stmt (1.0-1.3: )
Stack now 0 2
Entering state 72
Reducing stack by rule 5 (line 1366):
   $1 = nterm top_stmt (1.0-1.3: )
-> $$ = nterm top_stmts (1.0-1.3: )
Stack now 0 2
Entering state 71
Next token is token '\n' (1.3-1.3: )
Shifting token '\n' (1.3-1.3: )
Entering state 313
Reducing stack by rule 779 (line 5766):
   $1 = token '\n' (1.3-1.3: )
-> $$ = nterm term (1.3-1.3: )
Stack now 0 2 71
Entering state 315
Reducing stack by rule 780 (line 5769):
   $1 = nterm term (1.3-1.3: )
-> $$ = nterm terms (1.3-1.3: )
Stack now 0 2 71
Entering state 316
Reading a token: Now at end of input.
Reducing stack by rule 769 (line 5744):
   $1 = nterm terms (1.3-1.3: )
-> $$ = nterm opt_terms (1.3-1.3: )
Stack now 0 2 71
Entering state 314
Reducing stack by rule 3 (line 1353):
   $1 = nterm top_stmts (1.0-1.3: )
   $2 = nterm opt_terms (1.3-1.3: )
-> $$ = nterm top_compstmt (1.0-1.3: )
Stack now 0 2
Entering state 70
Reducing stack by rule 2 (line 1327):
   $1 = nterm $@1 (1.0-1.0: )
   $2 = nterm top_compstmt (1.0-1.3: )
vtable_free:12604: p->lvtbl->args(0x0000600002db0440)
vtable_free:12605: p->lvtbl->vars(0x0000600002db0460)
cmdarg_stack(pop): 0 at line 12606
cond_stack(pop): 0 at line 12607
-> $$ = nterm program (1.0-1.3: )
Stack now 0
Entering state 1
Now at end of input.
Shifting token "end-of-input" (1.3-1.3: )
Entering state 3
Stack now 0 1 3
Cleanup: popping token "end-of-input" (1.3-1.3: )
Cleanup: popping nterm program (1.0-1.3: )
```

# 全体を通しての感想
お昼はフィヨルドで一緒だったトミーさんとにしめさんととんかつを食べました。  
トミーさんとは長い間**ネットを通して話したことはあるけど**という関係性でした。初めてあったときにめっちゃ感動したってわけでもなく、「おぉ、実物だ！」くらいの意外と軽い感想でしたね。  
にしめさんは顔を見たことはなかったので、イメージと違ってびっくりしました。(元消防士と聞いていたので厳ついのをイメージしてた。)  
会議中は安定のフィヨルドコミュニティの皆さんとコミュニケーションを取りながら、卒業生のmasuyamaさんとお話できました。  
卒業生からの話を聞けるのは、自分が働くイメージをふくらませることができるので大変良い機会でした。  
懇親会ではigaigaさんにお世話になりつつ、「Rubyを書く人を増やしたい」「Rubyを盛り上げていきたい」という話を聞き、machidaさんとkakutaniさんの馴れ初めを聞いたりしており、大変楽しかったです。(お酒もお店での食事も大変最高でした！)  
関係者が多いのは本当にありがたいのですが、それに満足してしまって自分から話かけに行かないのでどこかの機会では知ってるけど面識ない人に積極的に話かけていきたいと思います。  
当日は日帰りだったので、福岡勢かつフィヨルドのメンターでもある@yuuuさんと鹿児島の夜の街を歩いたのは良い思い出になりました。  

最後に、オーガナイザーの皆さん、スタッフの皆さん、開催していただきありがとうございました。  
本当に楽しかったです！  
