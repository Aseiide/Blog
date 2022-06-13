---
title: "Σの式を多重ループを用いてRubyで書いてみる"
date: 2022-06-13T12:31:45+09:00
draft: false
summary: '苦手な多重ループの練習'
categories:
- 競プロ・アルゴリズム
tags:
- e8本
- 競プロ
- アルゴリズム
---

# 多重ループの練習
## 問題1

{{< img640x src="images/image1.png" alt="問題1" >}}

```ruby
ans = 0
for i in 1..3
  for j in 1..3
    ans += i * j
  end
end

puts ans
```

## 問題2

{{< img640x src="images/image2.png" alt="問題2" >}}

```ruby
ans = 0
for a in 1..4
  for b in 1..4
    for c in 1..4
      ans += a * b * c
    end
  end
end

puts ans
```
