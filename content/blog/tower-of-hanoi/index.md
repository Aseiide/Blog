---
title: "Rubyでハノイの塔を解く"
date: 2022-05-08T17:24:44+09:00
draft: false
summary: '「プログラマの数学」にでてきたハノイの塔をRubyで解く'
categories:
- 学習メモ
tags:
- プログラマの数学
- 数学
- ハノイの塔
---

最近、[プログラマの数学 第2版｜結城浩](https://www.hyuki.com/math/)を読んでいます。  
第6章「再帰」でハノイの塔が出てきて、それを解くプログラムが出てきたのでRubyで書いてみました。  
ハノイの塔が分からない人については調べてみてください。有名なので見たことある人は多いかも。  

## Ruby版ハノイの塔

```ruby
def hanoi(enban, from, to, via)
  if enban == 0
    puts '何もしない'
  elsif enban == 1
    puts "#{from} から #{to} へ移す"
  else
    hanoi(enban - 1, from, via, to)
    puts "#{from} から #{to} へ移す"
    hanoi(enban - 1, via, to, from)
  end
end

hanoi(5, 'A', 'B', 'C')
```

出力結果はこんな感じになります↓

```txt
A から C へ移す
A から B へ移す
C から B へ移す
A から C へ移す
B から A へ移す
B から C へ移す
A から C へ移す
A から B へ移す
C から B へ移す
C から A へ移す
B から A へ移す
C から B へ移す
A から C へ移す
A から B へ移す
C から B へ移す
```

全部で15行なので最短手数で解けてるはず。  
加えて、この[サイト](https://hanoi.aimary.com/)で出力通りに動かすと完成できたのであってると思う。  

## ひとこと

プログラマの数学読み物としてもプログラマの数学知識の復習にもなるので良いです。  
僕は数学Aの「組み合わせ」「確率」あたりが非常に苦手なのですが、答えというより数学的な捉え方や考え方が丁寧に書かれていて良いです。  
