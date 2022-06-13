---
title: "Rubyで階乗を求める"
date: 2022-06-13T12:24:06+09:00
draft: false
summary: 'Rubyで階乗を求める'
categories:
- 競プロ・アルゴリズム
tags:
- e8本
- 競プロ
- アルゴリズム
---

# Enumerable#inject を使った解き方

```ruby
n = gets.to_i
p (1..n).inject(:*)
```
# 再帰を使った解き方

```ruby
def factorial(n)
  if n < 0
    '負の数の階乗は計算できません'
  elsif n == 0
    return 1
  else
    n * factorial(n - 1)
  end
end

puts factorial(n)
```
## 参考

- [Rubyで階乗 - そぬばこ](https://nersonu.hatenablog.com/entry/2015/08/26/165828)
- [【Ruby のまずいコード】階乗 - Qiita](https://qiita.com/scivola/items/cc09eaa800623f69e955)
