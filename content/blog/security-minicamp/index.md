---
title: "セキュリティ・ミニキャンプ in 福岡 2020 に参加してきました"
date: 2020-10-18
draft: false
summary: "セキュリティ・ミニキャンプ in 福岡 2020 に参加したときの記録"
categories:
  - 技術
tags:
  - 勉強会
  - 技術
  - セキュリティ
---

# セキュリティ・ミニキャンプ in 福岡 2020　概要
[開催概要](https://www.security-camp.or.jp/minicamp/fukuoka2020.html)  
[公式の開催レポート](https://blog.security-camp.or.jp/posts/security-minicamp-fukuoka-2020-report/)

## 開催された講義
- Moving Target Defense基礎演習
- IoT機器を解析しよう！
- 情報セキュリティ技術の使い方をケースで考えよう
- Webアプリケーションの脆弱性体験

# 全体の感想
セキュリティ・ミニキャンプin福岡2020に参加してきました。  
日程は、10/11~10/12の2日間行われました。  
地元福岡での開催という事と、セキュリティについて講義形式で学ぶ機会が少ないので参加を決めました。  
非情報系なので、このミニキャンプは今後の学習のためになりました。  

参加者は18名で、中には中学生もいたみたいです。  
九大・九州内の大学生が多く参加していましたが、高知の学生や慶応の学生も居ました。  
男女問わず参加者が居たのも印象的でした。  

# 選考課題について
応募段階で、「志望動機」「リバースエンジニアリングの経験について記述」「python3を使ってプログラムを記述」課題がありました。  
志望動機は理論立てて、参加したい意思が伝わるように書くことを意識しました。  
リバースエンジニアリングの経験を問う課題については、経験がなかったので実際に置き時計を購入して分解し、考察した課題を提出しました。  
pythonのプログラムについては、簡単なwebアプリを作るものでpythonはほぼ書いたことがなかったので調べながら書いて提出しました。  

# Moving Target Defense 基礎演習
九大の小出先生による講義と演習でした。  
いわゆる低レイヤーの部分を触ったので、理解度は2割くらいです（悔しい）。単純に自分の知識不足です。  
セキュリティに関しては攻撃者そばが有利なので、攻撃者のコストを増やすための手法を学びました。  
実際に、カーネルをビルドしてシステムコールの番号を変更して挙動を確認しました。  


# IoT機器を解析しよう！
森瑛司(鹿児島大学理工学研究科)さんによる講義でした。  
普段の学習ではソフトウェアしか触っていないのでハードウェアを触る初めての機会となりました。  
実際の機器から基盤を取り出してはんだ付け。  
PCと接続してシリアル通信やUARTについて学習しました。  
ログを解析したり、他の班との違いなどを議論しました。  
ハードを触ると、電子回路の知識が必要になってくるので過去の実験の知識を思い出しながら取り組みました。  
かなり楽しかったので、ラズベリーパイやArduinoを触ってみようかなと思っています。  

# 情報セキュリティ技術の使い方をケースで考えよう
吉井和明弁護士による講義でした。  
技術者と法律は切っても切れない関係なので、法律の専門家から実際のケースを交えながらの講義は大変良かったです。  
特に今回のミニキャンプで学ぶ内容は深く学習すれば悪用できるので、「どうやって正しく使うのか」「どういった心がけであるべきなのか」技術者倫理について学びました。  
また、架空のケースとしてセキュリティ事案が発生したときにどのような順序で対応するのが良いか、実際に担当したことのある吉井先生から教えていただきました。  

# Web アプリケーションの脆弱性体験
猿渡翔一郎(株式会社セキュアサイクル)さんによる、講義・演習でした。  
OWASP TOP10に基づいて、webアプリケーションの脆弱性について学んだあと、講師が作ったアプリケーションの脆弱性を見つける演習をしました。  
XSSや、本来見えては行けないはずのデバック用の管理画面が見えたりなどの脆弱性を発見しました。  
実際に見つかった脆弱性に対して、どのような対策を施せばいいのかなど、応用のきく部分まで学習できました。  

# まとめ
今回のミニキャンプでは、web~法律~IoTなど普段の学習では触れない幅広いジャンルについて濃度高く学習できました。  
自分は年齢制限的に最初で最後の参加（セキュリティミニキャンプは25歳以下の学生が参加条件）となりましたが、参加してとても良かったです。  
講師の方々や、運営の方にはこのような機会を設けていただき感謝しています。  
