---
layout: post
title: "initializing dotfile repository"
date: 2013-01-04 21:52
comments: true
categories: dotfiles
---
今までdotfilesはdropboxに置いていて、新しいマシンに移る度にsymlinkして使ってきた。<br />
けど、去年の途中から職場が変わって

<!--more-->

* 作業環境がwindows(実際にはvm上のcentOS...)に移った
* dropboxが使えない環境になった<br />
 (本当は**githubも使えない**ひどい場所なんだけど、現在はproxy経由でなら一応アクセスできる)
* そうは言いつつ4・5ヶ月たって、場当たり的な設定がかなり増えてきた

ということで、ついに重い腰をあげてdotfilesをgitに移すべく作業中。

[konk303/dotfiles](https://github.com/konk303/dotfiles)

## やりたいこと

* zshの設定がもうどうにもならないぐらい汚いので、[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)を使って1回まっさらにする。その後、持ってきたい設定だけ追加で書いていくようにする
* .emacsも同様なので、こちらは[emacs starter kit](https://github.com/technomancy/emacs-starter-kit)を使う
  * ついでに**emacs24に完全移行**したい
* install.rb的なものを、rakeでなくthorで書いてみたい
* zsh/emacsどちらも、マシン別に固有の設定を書ける仕組を入れたい
  * 本当は ssh/configやproxy用netrcもそうしたいけど、こっちはpassword書くんでrepoには載せられないかな…
