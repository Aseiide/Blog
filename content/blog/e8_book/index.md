---
title: "E8本ID:009 復習"
date: 2022-06-09T14:55:51+09:00
draft: false
summary: '問題解決のための「アルゴリズム×数学」が基礎からしっかり身につく本 ID:009'
categories:
- 競プロ・アルゴリズム
tags:
- e8本
- 競プロ
- アルゴリズム
---

『問題解決のための「アルゴリズム×数学」が基礎からしっかり身につく本』の`問題ID:009`が自力では解けなかったので復習。  
なお、書籍名が長いので勝手に著者のidから取ってe8本と読んでいる。

# 問題

[009 - Brute Force 2](https://atcoder.jp/contests/math-and-algorithm/tasks/math_and_algorithm_i)

```txt
問題文
N 枚のカードが横一列に並べられています。左から i 番目 (1≤i≤N) のカードには整数 A 
iが書かれています。
カードの中からいくつかを選んで、合計がちょうど S となるようにする方法はありますか。

制約
1≤N≤60
1≤A 
i≤10000
1≤S≤10000
入力はすべて整数
```

# 回答

```ruby
n, s = gets.chomp.split.map(&:to_i)
a = gets.chomp.split.map(&:to_i)

n.times do |i|
  if a.combination(i).to_a.map(&:sum).include?(s)
    puts 'Yes'
    exit
  end
end

puts 'No'
```

# デバッグしながら考える

入力例1で考える
```
# 入力
3 11
2 5 9
```

## Array#combination

```ruby
n = 3
s = 11
a = [2, 5, 9]

# Enumeratorクラスのオブジェクトが返ってくる
n.times do |i|
  pp a.combination(i)
end
# <Enumerator: ...>
# <Enumerator: ...>
# <Enumerator: ...>
```
```ruby
# to_aを用いてarrayに変換
n.times do |i|
  pp a.combination(i).to_a
end
# [[]]
# [[2], [5], [9]]
# [[2, 5], [2, 9], [5, 9]]
```

```ruby
# 合計が必要なので合計の配列をつくる
n.times do |i|
  pp a.combination(i).to_a.map(&:sum)
end
# [0]
# [2, 5, 9]
# [7, 11, 14]
```

```ruby
# sが含まれているか確認
# 返り値がbooleanなことに注意
n.times do |i|
  if a.combination(i).to_a.map(&:sum).inclide?(s)
    puts 'Yes'
    # 見つかったら抜ける
    exit
  end
end

puts 'No'
```
