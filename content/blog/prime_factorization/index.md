---
title: "Rubyで素因数分解のプログラム"
date: 2022-06-15T15:27:44+09:00
draft: false
summary: Rubyで素因数分解するプログラムを書いた
categories:
- 競プロ・アルゴリズム
tags:
- e8本
- 競プロ
- アルゴリズム
---

# 素因数分解するプログラム

```ruby
n = gets.to_i
result = []
sqrt_n = Math.sqrt(n).to_i

(2..sqrt_n).each do |i|
  while n % i == 0
    n /= i
    result << i
  end
end

result << n if n >= 2
puts result.join(' ')
```

# 解説

以下の流れのようなアルゴリズムにすれば良い。

- `1 ~ sqrt(N)`まで調べる
- Nを2で割れるだけ割る
- Nを3で割れるだけ割る
- `sqrt(n)`まで同様の操作を続ける
- 最後に残ったNが2以上のとき、それを素因数に加える
