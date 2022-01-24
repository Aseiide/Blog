---
title: "UUIDとコンピュータとランダムネスについて"
date: 2022-01-22T19:07:59+09:00
draft: false
summary: 'RFCに定義されているUUIDの仕様とコンピュータとランダムネスについて'
slug: "uuid-randomness"
categories:
- 技術
tags:
- 技術メモ
- UUID
- 乱数
- 疑似乱数
- メルセンヌ・ツイスター
---

# UUID

- UUIDに関する仕様は RFC 4122 で公開されている
  - [rfc4122](https://datatracker.ietf.org/doc/html/rfc4122)
    - DeepLの翻訳を基にabstractのメモ
    - UUIDは128ビットの長さ
    - version1: 時間ベース
    - version2: DCEで定められたバージョン POSIX UUIDsに埋め込まれている
    - version3: 名前ベースのバージョン。このドキュメントで定められている。MD5ハッシュ関数を利用
    - version4: ランダムあるいは疑似ランダムに生成されたUUIDのバージョン。このドキュメントで定められている
    - version5:  名前ベースのバージョン。このドキュメントで定められている。SHA-1ハッシュ関数を利用

## RubyでUUIDを生成する方法

- [SecureRandom.uuid (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/method/SecureRandom/s/uuid.html)
- Rubyでは`securerandom`ライブラリを使うことでversion4のUUIDを生成できる

```ruby
require 'securerandom'
SecureRandom.uuid
#=> "7bac8e01-9928-4904-bcb4-de3f9e9926d1"
```

# コンピュータは真の乱数を生成できない？？

## 真の乱数とは？

サイコロを繰り返し振って得られるようなでたらめな数のこと。規則性や再現性がなく予測できない。

## コンピュータと乱数(ランダムネス)

コンピュータは人間がプログラムしたとおりに動き、それ以外の動作をしない機械だからランダムネスから最も遠いと言える

## コンピュータはどうやって乱数を生成しているのか？

- 疑似乱数を使っている
- Rubyは簡単に乱数を生成できる
- Random#rand を使用

```ruby
# Random#rand
irb(main):001:0> foo = Random.new(12345)
#=> #<Random:0x00007fc5d610cdb0>
foo.rand
#=> 0.9296160928171479
foo.rand
#=> 0.3163755545817859
```

## 疑似乱数とは？

- 乱数列の用に見えるが、実際には確定的な計算によって求められている疑似乱数列による乱数
  - 疑似乱数列を生成する機器を疑似乱数列生成器という
  - 生成するアルゴリズムを疑似乱数列生成法 という

### 疑似乱数列生成法(アルゴリズム)について

Rubyではメルセンヌ・ツイスタ(Mersenne Twister)というアルゴリズムによって疑似乱数を生成している

#### メルセンヌ・ツイスタ(Mersenne Twister) とは?

- 1996/97年に開発
- 従来の様々な生成法([* 古典的擬似乱数生成法])の欠点を考慮して設計されている
- 従来にない長周期、高次元均等分布
- 生成速度がかなり速い
- メモリ効率が良い

# 乱数/疑似乱数と暗号(きっかけだけ)

- 一般の疑似乱数はその方式と過去の出力が既知であれば、未来の出力を予測可能なので暗号の用途には不適である(暗号学的に安全ではない)
- 暗号理論では明確な定義が存在する
- Rubyには [module OpenSSL::Random (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/class/OpenSSL=3a=3aRandom.html) があって暗号論的に安全な乱数を生成できるっぽい,,

# Rubyのsecure random と random について

- [class Random (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/class/Random.html#S_RAND)
- [module SecureRandom (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/class/SecureRandom.html)

# 参照

- <https://ja.wikipedia.org/wiki/擬似乱数>
- [コンピュータとランダムネスの現状 - ペパボ研究所ブログ](https://rand.pepabo.com/article/2019/02/07/randomness/)
- [01gun_03hen_11.pdf](https://www.ieice-hbkb.org/files/01/01gun_03hen_11.pdf)
- [class Random (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/class/Random.html#S_NEW)
- [Mersenne Twister: A random number generator (since 1997/10)](http://www.math.sci.hiroshima-u.ac.jp/m-mat/MT/mt.html)

# 次回のためのキーワード

- 古典的疑似乱数生成法
- 古典的疑似乱数生成法の欠点
- 暗号論的擬似乱数生成機(CSPRNG)
