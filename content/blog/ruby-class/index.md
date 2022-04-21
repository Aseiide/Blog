---
title: "Rubyで数を扱うクラスについて調べてみた"
date: 2021-03-21
draft: false
summary: "RubyのFloat, to_f, BigDecimal, Rationalを調べた"
categories:
  - 技術
tags:
  - Ruby
  - 技術
  - 技術メモ
---

競プロをやる過程で小数の扱いがあったので深堀りしてみました。  
to_fメソッドをデカい小数で扱うときに丸め誤差が出てしまった。

# きっかけとなった事例

{{< img640x src="images/image1.png" alt="image1" >}}

僕が最初に提出したコードは以下

```ruby
x = gets.chomp.to_f
s = x.floor
puts s.to_i

# サンプルを試す
x = 84939825309432908832902189.9092309409809091329
# => 84939825309432916635287552 # 数値が丸まっているため正解できない

```

# RubyのFloatクラスについて

> 浮動小数点数のクラス。Float の実装は C 言語の double で、その精度は環境に依存します。  
一般にはせいぜい15桁です。詳しくは多くのシステムで採用されている浮動小数点標準規格、IEEE (Institute of Electrical and Electronics Engineers: 米国電気電子技術者協会) 754を参照してください。[リファレンスより引用](https://docs.ruby-lang.org/ja/latest/class/Float.html)

つまり、15桁までは浮動小数点として扱うことができ、16桁以上になると [IEEE754 規格](https://ja.wikipedia.org/wiki/IEEE_754)に従って数値が変換される。  
以下ではあるところから桁数が増えてるにも関わらず、数値が変換されていることがわかる。

また、メソッド`to_f`はIntegrでもStringでも使える。

## Integer#to_f

> self を浮動小数点数(Float)に変換します。  
selfがFloatの範囲に収まらない場合、Float::INFINITYを返します。[リファレンスより引用](https://docs.ruby-lang.org/ja/latest/method/Integer/i/to_f.html)


## String#to_f

> 文字列を 10 進数表現と解釈して、浮動小数点数 Float に変換します。  
浮動小数点数とみなせなくなるところまでを変換対象とします。変換対象が空文字列であれば0.0を返します。[リファレンスより引用](https://docs.ruby-lang.org/ja/latest/method/String/i/to_f.html)

## 浮動小数点とは
聞いたことあるけどなんだっけ。ってやつだったのであらためて学習した。  
数字を「仮数」「基数」「指数」で表す小数のこと。

[https://wa3.i-3-i.info/word14959.html]


# 任意の精度で10進数で表現された浮動小数点を扱えるBigDecimalについて
小数について調べていくうちにBigDecimalというライブラリがあることを知った。

## BigDecimalについて
BigDecimalを使うと桁数の多い小数でもきちんと扱える。  
※Stringとして渡す必要があることに注意。

> bigdecimal は浮動小数点数演算ライブラリです。任意の精度で 10 進表現された浮動小数点数を扱えます。[リファレンスより引用](https://docs.ruby-lang.org/ja/latest/library/bigdecimal.html)


```ruby
require "BigDecimal"

p BigDecimal("123.1234567890123456789") # => 0.1231234567890123456789e3
```

## どういうときにBigDecimalを使うのか
**Floatで扱える範囲を超えるかどうか** というのが基準になりそうな気がします。  

金額の計算では`BigDecimal`を使うのが良いみたいです

[https://qiita.com/jnchito/items/d0ef71b25732ad5a881c:title]

## 冒頭の問題をBigDecimalを使って解いてみた

```ruby
require 'bigdecimal'
 
x = gets.chomp # stringでxに格納
s = BigDecimal(x).floor # BigDecimalで浮動小数として扱って、小数点以下を切り捨て
puts s

# サンプルを試す
x = 84939825309432908832902189.9092309409809091329
# => 84939825309432908832902189

```

# おまけ（自戒）


[https://twitter.com/Aseiide/status/1373562468392267785:embed]


調べていくうちにコードを改善し、最終的には `to_f` も `BigDecimal` も使わず、 `to_i` でかいけつできた。  
脳死で.to_fやBigDecimalとするのではなく、to_iなども含めて適切なコードを使っていきたい。

# 番外編（追記）
Fukuoka.rbでお世話になっている [@udzura](https://twitter.com/udzura)さんよりコメントを頂きました。  
せっかくなのでRationalクラスについて追記していきます。

[https://twitter.com/udzura/status/1373590315647574017:embed]

# Rationalクラス
知らないクラスでした。  
競プロは知らないものに出会える良い機会だなと思っています。

> 有理数を扱うクラスです。  
「1/3」のような有理数を扱うことができます。IntegerやFloatと同様にRational.newではなく、 Kernel.#Rationalを使用してRationalオブジェクトを作成します。[リファレンスより引用](https://docs.ruby-lang.org/ja/latest/class/Rational.html)

```ruby
example.rb
Rational(1, 3)       # => (1/3)
Rational('1/3')      # => (1/3)
Rational('0.33')     # => (33/100)
Rational.new(1, 3)   # => NoMethodError
```

