---
title: "[復習]ABC253 A問題B問題"
date: 2022-05-29T15:48:52+09:00
draft: false
summary: AtcoderBeginnerContest253の復習
categories:
- 技術
tags:
- atcoder
- 競プロ
---

[問題 - NOMURA プログラミングコンテスト2022（AtCoder Beginner Contest 253）](https://atcoder.jp/contests/abc253/tasks)

こちらのA問題は微妙な解き方、B問題は解けなかったので復習

## A問題
[A - Median?](https://atcoder.jp/contests/abc253/tasks/abc253_a)

```
問題文
整数 a,b,c が与えられます。b がこれらの整数の中央値であるかどうか判定してください。

出力
b が与えられた整数の中央値であるならば Yes、そうでないならば No と出力せよ。
```

### 解法1(自分の提出したコード)

- 考え
  - 小さい順に並べた配列のindexが1のものがbと一致すれば中央値となるので以下のコードで提出
- イケてないポイント
  - 分割で変数に代入して新たに配列にしている点

```ruby
a, b, c = gets.chomp.split.map(&:to_i)
ary = [a, b, c].sort

if ary[1] == b
  puts 'Yes'
else
  puts 'No'
end
```

### 解法2(解説をもとに)

- 中央値の条件
  - a,b,c を降順に並べたときに2番目にくること
    - `a <= b <= c または c <= b <= a`ならば`Yes`そうでないなら`No`となる
      - この条件がパッと思いつかなかった

```ruby
a, b, c = gets.chomp.split.map(&:to_i)

if (a <= b && b <= c) or (c <= b && b <= a)
  puts 'Yes'
else
  puts 'No'
end
```

## B問題

[B - Distance Between Tokens](https://atcoder.jp/contests/abc253/tasks/abc253_b)
問題文は省略

こういう問題、すごく苦手なので解説を見ながら実装していく

- 分からなかった点
  - 距離の計算方法
    - 中学数学とかの復習(?)
    - `a行目b列目のコマ`と`c行目d列目のコマ`の距離
      - `(a-cの絶対値) + (b-dの絶対値)`で計算できる
  - 入力`---o`の受け取り方
    - `ary = ["--o", "o--"]` このとき、`ary[0][2] #=> o` にアクセスできるので
    - `["--o", "o--"]`こういう形で受け取ればOK
    - 配列なのでコマの位置を入力例1だったら`[2, 0], [0, 1]`という形で受け取る

### 解法

```ruby
h, w = gets.chomp.split.map(&:to_i)
s = h.times.map{ gets.chomp}

xs = [] # 一つのコマの位置
ys = [] # もうひとつのコマの位置

h.times do |y|
  w.times do |x|
    if s[y][x] == 'o'
      xs << x
      ys << y
    end
  end
end

#=> xs = [2, 0]
#=> ys = [0, 1]

puts ((ys[0] - ys[1]).abs + (xs[0] - xs[1]).abs)
```
