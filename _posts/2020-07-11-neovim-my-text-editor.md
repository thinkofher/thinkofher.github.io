---
title: "Neovim as my main text editor"
subtitle: "Keep doing stuff inside terminal emulator, part one: text editing."
author: thinkofher
website: "https://github.com/thinkofher"
tags: editor vim unix
layout: post
---

I am mainly using [Neovim](https://neovim.io/) as my text editor. Neovim offers both speed, extensibility and feeling of using modern text editor. Neovim is fully compatible with Vim and its plugins, so you don't have to worry about it, if you're a regular Vim user and thinks about switching. You can also check `:help nvim-from-vim` manual, after Neovim installation.

### Why Vim over Neovim?

There are plenty of reasons to use Neovim over Vim. Here are some.

#### Neovim ships as AppImage

No installation is needed. You can just download Neovim as AppImage from their [releases](https://github.com/neovim/neovim/releases) section, move it to some directory in your `$PATH`, make it executable and start using it. Everything is packed into self mounting container. This is a killer feature for a Linux user like me. I have been using Neovim this way since Aug 2019 and have never had any troubles.

#### It's all about maintenance

Neovim is a true open source project with a great community. They've got plenty of contributors from all over the world. Neovim has become quite a large project in recent years and it's getting even bigger, in a similar way to Visual Studio Code. The main difference is that, there is no large and malicious corporation behind Neovim.

#### Nightly, who cares?

To be honest, I am not only using Neovim as AppImage. I am using Neovim as AppImage in nightly version. I can't complain. It's really stable. Every plugin that I am using currently is working fine and I've got access to bleeding edge features. I even wrote a [script](../scripts/nvim-up) to download newest Neovim version.

#### LSP out of the box

At the time of writing this post, lsp api for Neovim is working really well. I even have switched lsp client that I was using for a while from [LanguageClient-neovim](https://github.com/autozimu/LanguageClient-neovim) to [built-in](https://github.com/neovim/nvim-lsp). Keep this in mind if you're going to use my [dot files](https://github.com/thinkofher/dotfiles). Read more about built-in lsp [here](https://neovim.io/doc/user/lsp.html) or just use `:help lsp` command in your Neovim.

#### Read more

- [Neovim visions.](https://neovim.io/charter/)
- [You can write plugins for Neovim in any programming language.](https://github.com/neovim/neovim/wiki/Related-projects#api-clients)
- [Lua language is built-in into Neovim.](https://neovim.io/doc/user/lua.html)
- [Platform agnostic.](https://github.com/neovim/neovim/wiki/Introduction#platform-specific-code)
