---
layout: post
title: 为 Markdown 生成 TOC 的 Vim 插件
categories: Vim
description: 为 Markdown 自动生成 Table of Contents 的 Vim 插件
keywords: vim, markdown, toc
---

因为饱受 GFM 和 Redcarpet 两种 Markdown 引擎生成 TOC 链接的差异的折磨，而我又不得不同时使用它们——博客基于 Jekyll 使用 Redcarpet（*Update 2016/09/16: GitHub Pages 现在已经改为只支持 kramdown*），而其它放在 GitHub 仓库里的文档使用 GFM，我决定为我常用的 Markdown 编辑器 Vim 做一款同时支持 GFM 和 Redcarpet 两种 TOC 链接风格的 Table of Contents 自动生成插件。

这算是我真正意义上完全独立开发的第一款实用 Vim 插件，当然开发过程中也参考了别人的做法。

## 下载地址

* [vim-markdown-toc](https://github.com/mzlogin/vim-markdown-toc)

## 功能

* 为 Markdown 文件生成 Table of Contents，目前支持 GFM 和 Redcarpet 两种链接风格。

* 更新已经存在的 Table of Contents。

* 保存文件时自动更新 Table of Contents。

## 使用方法

### 生成 Table of Contents

将光标移动到想在后面插入 Table of Contents 的那一行，然后运行下面的某个命令：

1. `:GenTocGFM`

   生成 GFM 链接风格的 Table of Contents。

   适用于 GitHub 仓库里的 Markdown 文件，比如 README.md，也适用用于生成 GitBook 的 Markdown 文件。

2. `:GenTocRedcarpet`

   生成 Redcarpet 链接风格的 Table of Contents。

   适用于使用 Redcarpet 作为 Markdown 引擎的 Jekyll 项目或其它地方。

### 更新已存在的 Table of Contents

通常不需要手动做这件事，保存文件时会自动更新已经存在的 Table of Contents，如果必须手动更新的话，使用 `:UpdateToc` 命令。

## 安装方法

推荐使用 [Vundle](http://github.com/VundleVim/Vundle.Vim) 来管理你的 Vim 插件，这样你就可以简单三步完成安装：

1. 在你的 vimrc 文件中添加如下内容：

   ```
   Plugin 'mzlogin/vim-markdown-toc'
   ```

2. `:so $MYVIMRC`

3. `:PluginInstall`

使用 vim-plug 安装的过程的与此基本一样。

## 配置选项

1. `g:vmt_auto_update_on_save`

   默认值：1

   插件会自动更新已经存在的 Table of Contents，如果你不想要这个功能，可以在你的 vimrc 文件里加入如下内容关闭：

   ```viml
   let g:vmt_auto_update_on_save = 0
   ```

2. `g:vmt_dont_insert_fence`

   默认值：0

   在默认情况下，`:GenTocXXX` 命令会在插入的 Table of Contents 前后加上 `<!-- vim-markdown-toc -->`，这是为了实现保存时自动更新 Table of Contents 功能。

   如果你不想看到它们，可以在 vimrc 文件里加入如下内容移除：

   ```viml
   let g:vmt_dont_insert_fence = 1
   ```

   需要注意的是移除之后插件将无法再帮你保存文件时自动更新 Table of Contents 了。

## 屏幕截图

[使用本插件生成 TOC 的英文文档在线示例](https://github.com/mzlogin/chinese-copywriting-guidelines/blob/Simplified/README.en.md)

![](https://github.com/mzlogin/vim-markdown-toc/raw/master/screenshots/english.gif)

[使用本插件生成 TOC 的中文文档在线示例](http://mazhuang.org/wiki/chinese-copywriting-guidelines/)

![](https://github.com/mzlogin/vim-markdown-toc/raw/master/screenshots/chinese.gif)

## 参考链接

* [GFM 与 Redcarpet 的不同点](http://mazhuang.org/2015/12/05/diff-between-gfm-and-redcarpet/)
* [ajorgensen/vim-markdown-toc](https://github.com/ajorgensen/vim-markdown-toc)
