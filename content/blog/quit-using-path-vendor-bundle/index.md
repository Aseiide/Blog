---
title: "改めてbundle install --path vendor/bundleはやめよう"
date: 2022-02-17T23:01:48+09:00
draft: false
summary: 'bundle install にオプションは不要っぽいという話'
categories:
- 技術
tags:
- Rails
- フィヨルドブートキャンプ
---

# Gem::LoadErrorで急に開発環境が壊れた

現在、フィヨルドブートキャンプで「システム開発」に取り組んでいます。
開発をしようとminitestを実行しようとしたところ、`Gem::LoadError`となり実行できなくなりました。

# TL;DR

[bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう - Qiita](https://qiita.com/jnchito/items/99b1dbea1767a5095d85)
を読んで、`--path vendor/bundle`をつけるのはやめるのと、設定を見直しましょう。

## 発生したエラー

以下のようなエラーで、出力を見る限りstringioが原因みたい。
Gemfileには`stringio 3.0.1`を読み込むようになっているが、ローカルの環境では`stringio 0.1.0`でセットアップされちゃってるよ、ということでした。

```
❯ bin/rails test test/system/notification/tabs_badges_test.rb
/Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/runtime.rb:309:in `check_for_activated_spec!': You have already activated stringio 0.1.0, but your Gemfile requires stringio 3.0.1. Since stringio is a default gem, you can either remove your dependency on it or try updating to a newer version of bundler that supports stringio as a default gem. (Gem::LoadError)
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/runtime.rb:25:in `block in setup'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/spec_set.rb:136:in `each'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/spec_set.rb:136:in `each'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/runtime.rb:24:in `map'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/runtime.rb:24:in `setup'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler.rb:150:in `setup'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/setup.rb:10:in `block in <top (required)>'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/ui/shell.rb:136:in `with_level'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/ui/shell.rb:88:in `silence'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems/bundler-2.2.30/lib/bundler/setup.rb:10:in `<top (required)>'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/2.7.0/rubygems/core_ext/kernel_require.rb:83:in `require'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/2.7.0/rubygems/core_ext/kernel_require.rb:83:in `require'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/commands.rb:33:in `<module:Spring>'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/commands.rb:4:in `<top (required)>'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/2.7.0/rubygems/core_ext/kernel_require.rb:83:in `require'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/2.7.0/rubygems/core_ext/kernel_require.rb:83:in `require'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/application.rb:87:in `preload'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/application.rb:157:in `serve'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/application.rb:145:in `block in run'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/application.rb:139:in `loop'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/application.rb:139:in `run'
from /Users/aseiide/development/fjordbootcamp/bootcamp/vendor/bundle/ruby/2.7.0/gems/spring-2.1.1/lib/spring/application/boot.rb:19:in `<top (required)>'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/2.7.0/rubygems/core_ext/kernel_require.rb:83:in `require'
from /Users/aseiide/.rbenv/versions/2.7.4/lib/ruby/2.7.0/rubygems/core_ext/kernel_require.rb:83:in `require'
from -e:1:in `<main>'
```

# 結局、gem install stringio -v 3.0.1 で解決

ログを見る限りは、`stringio 3.1.0`が必要ということだったので`gem install stringio -v 3.0.1`を実行しインストールしました。
そうしたところ、エラーは直り開発環境が無事に立ち上がるようになりました。

# なぜgemのインストールで解決したのか？？

 そもそも、原因は以下のように推測されるようです。

1. テストを実行しようとする
2. まずBundlerに処理が移る
3. Bundler本体が？Rubygemsが？require 'stringio'する。このタイミングではRuby 2.7標準の(=default gemの)stringio 0.1.0が読み込まれる
4. Bundlerが？Railsが？Gemfile.lockの内容に従ってgemをrequireしていく。
5. Gemfile.lockではstringio 3.0.1が指定されているのでこれをrequireしようとする。しかし、stringio 0.1.0がすでに読み込まれており、バージョンが異なるのでどちらを正とすべきか判断できない
6. Bundlerはstringioの読み込みを諦めて "You have already activated stringio 0.1.0, but your Gemfile requires stringio 3.0.1. Since stringio is a default gem" というエラーメッセージを出して異常終了する

`gem install stringio -v 3.0.1`でインストールすると、3で最新のgemを読み込むことになり、5でのバージョンの差異が発生せず、正常に起動できるようになった。

この原因に関しては、フィヨルドブートキャンプ内のQ&Aを使って、メンターの[@jncito](https://twitter.com/jnchito)さんが教えてくださいました。

プロジェクトのローカルにしか`stringio 3.0.1`が入っておらず。3で`stringio 3.0.1`が読み込まれて欲しいのに、`stringio 0.1.0`が読み込まれていたということになります。

# タイトル回収

ではなぜ、プロジェクトのローカルにしか`stringio 3.0.1`が入っておらず、システム(PC全体)に入っていなかったのか？？
`bundle install --path vendor/bundle`の設定が残っていたためでした。
[bundle install時に--path vendor/bundleを付ける必要性は本当にあるのか、もう一度よく考えてみよう - Qiita](https://qiita.com/jnchito/items/99b1dbea1767a5095d85)を読んで以降、`bundle install`はオプション無で実行するようにしていましたが、以前はいプションを付けていたのでその時の設定が残っていたために、`bundle install --path vendor/bundle`をしたのと同じ挙動になっていたようです。

## bundle install --path vendor/bundle の設定が残っているか確認する方法

```
cat .bundle/config
cat ~/.bundle/config
```

これらを実行して、出力結果に`BUNDLE_PATH: "vendor/bundle"`があったら設定が残ってしまっていますので、消すのが良さそうです。

```
bundle config --delete path
bundle install

# この状態でも問題なく動作することを確認する
# vendor/bundleは不要なので削除
rm -rf vendor/bundle

# 念のためもう一度動作確認する。問題なく動けば設定変更完了
```

# ひとこと(ちょっと宣伝)

フィヨルドブートキャンプのメンターやアドバイザーにはRubyに詳しい人が多く、質問をするといい感じにヒントをもらったり教えてもらったり、ペアプロできたりするのでオススメです。
