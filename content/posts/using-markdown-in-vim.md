---
title: "Using Markdown in Vim"
author: Jacob Goldstein
date: 2021-01-04T09:05:39-05:00
draft: false
type: post
categories:
 - vim
 - linux
tags:
 - vim
 - linux
---

If you _are_ working with something that works like [CommonMark](https://commonmark.org/) and does _not_ insert a `<br>` for every newline character then you'll probably want to display trailing spaces, so that you know when you actually have the two trailing spaces needed to insert a `<br>`. See [Showing Invisible Things In Vim](/2019/03/12/showing-invisible-things-in-vim/) for how to do this.

## Troubleshooting

In the course of writing this I encountered a number of problems.

Terminal Vim displayed a background color for italic text and bold text was bolded, but in my Gui Vim they both just looked like all the other text. It turned out the problem was my font.

Once I told it to stop using the offending font the bold text became bolded and the italic text was italic. I installed and tried a number of fonts before I found one that worked and I enjoyed the look of. It was [Roboto Mono](https://fonts.google.com/specimen/Roboto+Mono) by Christian Robertson.

A common thing with Markdown plugins is to muck with the `conceallevel` (see above). They _seem_ to want to set it to 2 which hides bold and italic formatting characters entirely. Personally, I hate it when my editor is hiding things I typed without asking. If the plugin doesn't have a configuration for this you may have to add a `set conceallevel=0` line to your [~/.vimrc](/2019/03/03/editing-your-.vimrc-file/). Preferably _after_ the section where plugins are loaded.

## Markdown Plugins

One of the most common requests is for the ability to preview your markdown as you type it. Vim can't do that internally, but you can wire it up to external tools. Most of them watch for changes to your file, run it through a markdown to html conversion, and open it up in your browser window.

I'm a Mac user so I can leverage the spectacular [Marked 2](https://marked2app.com/) markdown preview app. With the help of the [marked.vim](https://github.com/itspriddle/vim-marked) plugin I can type `:MarkedOpen` and the file I'm currently working on opens up in Marked. Every time I save it, Marked handles re-rendering it (in a variety of flavors). If you're on the Mac and you write a lot of Markdown I highly recommend buying Marked.

What follows are links to ones I've found. I recommend a pause for thought before installing any of them. You must consider what rendering engine they're using. A lot of them seem to render [GitHub Flavored Markdown](https://github.github.com/gfm/) which handless newlines differently than [CommonMark](https://commonmark.org/).

* [vim-instant-markdown](https://github.com/suan/vim-instant-markdown) requires Nodejs for rendering. Renders GitHub flavored Markdown. - macOS, Linux, Windows
* [vim-markdown-preview](https://github.com/JamshedVesuna/vim-markdown-preview#readme) can use Markdown _or_ grip to give you Common Mark and GFM - macOS, Linux
* [markdown-preview.vim](https://github.com/iamcco/markdown-preview.nvim) requires Vim >= 8.1 or Neovim. This supports a number of interesting markdown extensions like [mermaid](https://github.com/knsv/mermaid),[chart.js](https://github.com/chartjs/Chart.js). It's not clear what the core Markdown flavor is. - macOS & Linux?

* [previm](https://github.com/previm/previm) requires Python 2.7.5 and supports CommonMark and PHP Markdown
* [livedown.vim](https://github.com/shime/vim-livedown) requires the Livedown npm module. It's not clear what Markdown flavor it supports

You don't actually need a plugin to render Markdown and load it in the browser. [This Reddit post](https://www.reddit.com/r/vim/comments/8asgjj/topnotch_vim_markdown_live_previews_with_no/) shows examples of a Vim function that can use whatever rendering engine you want.

Personally, I'll just use a plugin.

[mkdx](https://github.com/SidOfc/mkdx) is a [Swiss Army Knife](https://en.wikipedia.org/wiki/Swiss_Army_knife) for people who love Markdown. It also supports things from markdown variants like [Github Flavored Markdown](https://github.github.com/gfm/). For example, it can highlight "checkboxes" and "tables". Two things which don't normally exist in markdown.

An example feature that I find useful is the ability to create a link out of any visually selected text. For example if you [visually selected](/2019/03/03/vims-visual-mode/) "foo" in

```
The word foo is a metasyntactic variable.

```

and then typed `<leader>ln</leader>` mkdx would convert it to

```
The word [foo]() is a metasyntactic variable.

```

and move your cursor between the parentheses and switch to insert mode. mkdx is filled with lots of little features like that. It also supports things like highlighting "checkboxes" and tables from GFM.

[vim-markdown](https://github.com/plasticboy/vim-markdown) adds support for GFM, fenced code block languages for syntax highlighting within them, LaTeX math, YAML Front Matter, TOML Front Matter, JSON Front Matter, Strikethroughs, and more.

When creating ordered (numbered) lists, it's just a matter of time before you find yourself needing to reorder them, or inserting a new item in the middle. Editing all those numbers is annoying. That's where [vim-renumber](https://github.com/clarke/vim-renumber#readme) comes in.

It'll convert

```
3. baz
1. foo
2. bar
```

```
1. baz
2. foo
3. bar
```

Vim acts as if text was never folded when you tell a GUI client to print. The suggested workaround is to use the `:TOhtml` command that generates an HTML version of the current window, save that in a file, open that in a browser, and then print from the browser.

