---
layout: post
title: "moved from rvm to rbenv"
date: 2013-01-05 11:41
comments: true
categories: rbenv
---
[rvm](https://rvm.io/)から[rbenv](https://github.com/sstephenson/rbenv)に移った。<br />
ミニマルでなかなか良い感じ。

いつものようにreadline問題で最初irbが日本語受け入れなかったけど、configureのoptionで無事解決。

<!--more-->

### インストール

* `brew install brew install rbenv ruby-build`
* `echo 'eval "$(rbenv init -)"' >> ~/(.bash_profile|.zshenv)`
* `rbenv install 1.9.3-p362`<br />
  これで一応入るんだけど、readlineで日本語がNGだったので
* `rm -rf ~/.rbenv/versions/1.9.3-p362`<br />
(削除はこれだけ)
* configureにオプション追加([ruby-build](https://github.com/sstephenson/ruby-build)にインストール時の設定等書いてある)<br />
`CONFIGURE_OPTS="--with-readline-dir=$(brew --prefix readline)" rbenv install 1.9.3-p362`
* コマンド(irbとかrakeとか)を使用するためにはrehashが必要<br />
`rbenv rehash`
* `rbenv global 1.9.3-p362`<br />
(.rbenv/versionに"1.9.3-p362"が書き込まれるだけ)

これでオーケー。
    $  ruby --version
    ruby 1.9.3p362 (2012-12-25 revision 38607) [x86_64-darwin12.2.0]

### 感想

* gemの管理は、bundler使うようになってからは完全に不要になった。gem listが汚くても全然困らない。<br />rvmのgemsetは最初便利だと思ったけど、bundler登場後はただ面倒くさいだけだった。
* バージョンを必ずパッチレベルまで指定しないといけないのがrvmに比べるとちょっと不便。<br />
例えば[octopress](https://github.com/imathis/octopress)は1.9.3-p194で固定してあって、絶対p362でも動くんだけどp194を使うか.ruby-versionを書き換えないといけない。
* 37signalsの人が作るものは、何か同じ匂いがしますね、powとか。シンプルで簡素で、必要な仕事を完璧にこなす。<br />ドキュメントが簡素すぎじゃぁ?と入れる前は思うんだけど、結局ドキュメントを読む必要がほとんどない(デフォルトがきれいだし、詰まった時はコード読んだほうが早い)。