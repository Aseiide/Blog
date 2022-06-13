---
title: "Rubyで素数を判定するプログラム"
date: 2022-06-13T12:28:48+09:00
draft: false
summary: 'Rubyで素数を判定するプログラム'
categories:
- 競プロ・アルゴリズム
tags:
- e8本
- 競プロ
- アルゴリズム
---

# primeライブラリを使わずに解く

```ruby
n = gets.to_i

def prime?(n)
  if n == 1
    return false
  end
  2.upto(Math.sqrt(n)) do |i|
    return false if n % i == 0
  end
  true
end

(1..n).each do |k|
  if prime?(k)
    print "#{k} "
  end
end

# 入力 10
#=> 2 3 5 7
```

# primeライブラリを使って解く

```ruby
require 'prime'
n = gets.to_i

(1..n).each do |k|
  if Prime.prime?(k)
    print "#{k} "
  end
end

# 入力 10
#=> 2 3 5 7
```
