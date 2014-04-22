---
layout: post
title: "How I switched from bash to (oh-my) zsh"
date: 2012-05-08 10:00
comments: true
tags:
- tools
- productivity
---

I switched from `bash` to `zsh` lately. After [announcing it on Twitter](https://twitter.com/ctrabold/status/196899229455753216) I got lots of reactions, mostly questions, how I did get started.

## So here's how I got started:

1. I *decided* to change my shell. Why? Actually I was like *why not?* Seeing a lovely bunch of hackers at the [Vagrant Usergroup Berlin](https://twitter.com/berlinvagrant) getting excited with [`tig`](https://git.wiki.kernel.org/index.php/Tig) (a Git browser on the shell) can have quite an influence - so I though: *there's got to be more than my standard shell!*
1. I did `brew install zsh` to get the latest version
1. I added `/usr/local/bin/zsh` to `/etc/shells` Otherwise you won't be able to activate the shell.
1. Finally I switched the shell to zsh: `chsh -s /usr/local/bin/zsh`

After that I removed `~/.bash-it`, followed the instructions [`https://github.com/robbyrussell/oh-my-zsh`](https://github.com/robbyrussell/oh-my-zsh) and customized my `~/.zshrc`.

That's it.

Since then I do not regret it. I feel very comfortable with my new shell and I love the tiny little features it provides like auto-completion and correction.

I didn't dig into scripting yet though, so I can't provide any feedback here but would love to hear your optinion on this.

## References

* [https://github.com/robbyrussell/oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) – A community-driven framework for managing your zsh configuration
* [http://zsh.sourceforge.net/Guide/](http://zsh.sourceforge.net/Guide/) – A User's Guide to ZSH
* [http://zsh.sourceforge.net/Doc/](http://zsh.sourceforge.net/Doc/) – ZSH Documentation
* [http://grml.org/zsh/](http://grml.org/zsh/) – A collection of usefull scripts via [@mikagrml](https://twitter.com/#!/mikagrml/status/199127345968320512)
