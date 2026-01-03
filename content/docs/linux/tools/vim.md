---
title: "Vim 技巧"
weight: 1
bookFlatSection: false
bookToc: true
bookHidden: false
bookCollapseSection: false
bookComments: false
bookSearchExclude: false
bookHref: ''
bookIcon: ''
---


VIM 命令
=====

### 基础操作

`h`、 `j`、 `k`、 `l` 移动光标

`w`、`e` 、`b` 按单次移动光标

`gg` 跳转到文件开头

`G` 跳转到文件末尾

`Ctrl-U`、`Ctrl-D`、`Ctrl-E`、`Ctrl-Y`、`Ctrl-B`、`Ctrl-F`卷动屏幕
`d` 删除，  `c` 修改， `y` 复制，`p` 粘贴

`i` 、`a` 进入编辑模式

### 配置

可以编辑`.vimrc`文件，对vim进行配置，命令 `vim .vimrc`

```bash
set ruler
set number
set showcmd
set showmode
set laststatus=2
set cmdheight=2
```

### Window

`:split`  `:vsplit` 分割窗口

`ctrl-w j` `ctrl-w k` 上下移动窗口，同时`h` `l左右切换窗口`

`:only` 只显示当前窗口

如果需要使 *有修改未保存的* 窗口隐藏，可以在`.vimrc`中添加 `set hidden`

`:Explore ~` 显示目录树，`:Vex` 在侧边栏显示目录树，用上面的命令切换窗口。选择文件按回车会在目录窗口打开文件，如果在文件上按 `p` 会在一个新窗口中打开文件。

`:buffers!`  或者 `:ls!` 显示切换到后台的 buffer，也就是切换到后台的窗口。叫buffer是因为当前打开内容只是在内存中，还没有写入磁盘。

`:buffer 1`  切换到窗口未 1 的buffer

`:tabnew` 创建一个标签页，后面可以加名字给标签页命名，`:tabclose` 关闭标签页。

`gt`  和 `gT` 切换标签页。`:tabs` 查看所有标签页，`:tabmove` 调整标签页顺序。

### 搜索

- `/` 搜索

```shell
/isTestSource="true"
```

直接输入/ + 字符串，然后按回车
之后按n跳转到下一个匹配
按N跳转到上一个匹配

`*`跳转到光标所在单词的下一个匹配
`#`跳转到光标所在单词的上一个匹配

- 查看所有匹配

```shell
:g/isTestSource="true"/#
:g/字符串/p  #显示所有匹配的行（无行号）
:g/字符串/=  # 显示行号但不显示内容
```

- 搜索并删除

```shell
:g/isTestSource="true"/d  
:g/字符串/  #仅匹配不执行操作
:g/字符串/dc  #删除没一行前询问
```

- 高亮

```shell
:match Search /.*字符串.*/    #高亮所有匹配的行
```

- 搜索并替换

```shell
:s/old/new/      #将当前行中第一个匹配的old替换为new
:s/old/new/g     #将当前行中所有匹配的old替换为new
:%s/old/new/g    #在整个文件范围内替换所有匹配的old为new
:5,10s/old/new/g  #在第5行到第10行范围内替换所有匹配
```

