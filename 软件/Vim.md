## 介绍

* 名字：Vim
* 语言：英文
* 平台：Windows
* 翻译：语言包
* 类型：文本编辑
---
* 评分：10
* 评价：Vim 是一种哲学。
* 封面：
![](./Vim.md.files/-2091442061.1.avif)
* 图片：
![](./Vim.md.files/PixPin_2025-04-16_04-03-16.avif)
* 简介：Vim 是一个类似于 Vi 的高度可定制的文本编辑器，在 Vi 的基础上改进和增加了很多特性。
---
* 现文件名：\[gVim]\[9.1.0]\[CHS].7z
* 原文件名：
	* gvim_9.1.0_x86_signed.exe
	* gvim_9.1.0_x64_signed.exe
* 大小：
	* 9.8912 MB
	* 10.4535 MB
* 散列：
	* 6B0282FDFA28AA2858D22BC2D5CC6F56
	* C9791F723EAD996CEE2B96AE5ACB6B11
* 引用页：https://www.vim.org/download.php
* 主链接：
	* https://github.com/vim/vim-win32-installer/releases/download/v9.1.0/gvim_9.1.0_x86_signed.exe
	* https://github.com/vim/vim-win32-installer/releases/download/v9.1.0/gvim_9.1.0_x64_signed.exe
* 标准链接：
	* ed2k://|file|gvim_9.1.0_x86_signed.exe|10371624|6B0282FDFA28AA2858D22BC2D5CC6F56|h=QONVG6E6UPSSSZL7EPDRVRO5WRVMBPQ5|/
	* ed2k://|file|gvim_9.1.0_x64_signed.exe|10961248|C9791F723EAD996CEE2B96AE5ACB6B11|h=UNMTBK67Y37CBVIE2RMHR4AZDOHAMEH7|/
* 下载方式：浏览器

## 安装方法

* 运行“gvim_9.1.0_x64_signed.exe”安装。

## 使用技巧

### 设置

Vim 的配置文件在安装目录下的“\_vimrc”。它没有后缀名，但其实是个文本文件。可以用编辑器打开。

这是我个人向设置：

```
set autoread " 自动更新，当文件在外部被修改时。
set autowrite  " 自动保存。
set clipboard+=unnamed " 共享剪切板。
set nobackup  " 不备份。
set noundofile  " 无撤销文件。
set noswapfile  " 无 swap 文件。
set noexpandtab  " 避免“<Tab>”转为空格。
set wrap  " 自动换行。
set hlsearch  " 搜索时高亮。
set ignorecase  " 查找大小写不敏感，
set smartcase  " 如果有一个大写字母则切换到大小写敏感查找。
set guifont=Cascadia\ Mono:h18    " 设置字体。
set number  " 设置行号。
set ruler  " 显示标尺。
set showmatch  " 高亮显示匹配的括号。
set ambiwidth=double " 设置为双倍字符宽度。

let mapleader=" `" " 设置先导键为“`”。

syntax enable  " 自动开启语法高亮。

autocmd VimEnter * :startinsert " 预设编辑模式。

" 预设为窗口最大化。
if has('win32') || has('win64')    
	au GUIEnter * simalt ~x
else    
	au GUIEnter * call MaximizeWindow()
endif 
function! MaximizeWindow()    
	silent !wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
endfunction

" 上移一个屏幕行，若无法移动，则跳到行首。
function! MoveUp()
  let [old_line, old_col] = [line('.'), col('.')]
  normal! gk
  if [line('.'), col('.')] == [old_line, old_col]
    normal! ^
  endif
endfunction

" 下移一个屏幕行，若无法移动，则跳到行尾。
function! MoveDown()
  let [old_line, old_col] = [line('.'), col('.')]
  normal! gj
  if [line('.'), col('.')] == [old_line, old_col]
    normal! $
  endif
endfunction

" 左移一个字符，若无法移动，则跳到上一行末尾。
function! MoveLeft()
  let [old_line, old_col] = [line('.'), col('.')]
  normal! h
  if [line('.'), col('.')] == [old_line, old_col]
    normal! gk$
  endif
endfunction

" 右移一个字符，若无法移动，则跳到下一行行首。
function! MoveRight()
  let [old_line, old_col] = [line('.'), col('.')]
  normal! l
  if [line('.'), col('.')] == [old_line, old_col]
    normal! gj^
  endif
endfunction

" 移动映射
nnoremap <silent> <Up> :call MoveUp()<CR>
inoremap <silent> <Up> <C-o>:call MoveUp()<CR>
snoremap <silent> <Up> :call MoveUp()<CR>
vnoremap <silent> <Up> :call MoveUp()<CR>
nnoremap <silent> <Down> :call MoveDown()<CR>
inoremap <silent> <Down> <C-o>:call MoveDown()<CR>
snoremap <silent> <Down> :call MoveDown()<CR>
vnoremap <silent> <Down> :call MoveDown()<CR>
nnoremap <silent> <Left> :call MoveLeft()<CR>
inoremap <silent> <Left> <C-o>:call MoveLeft()<CR>
snoremap <silent> <Left> :call MoveLeft()<CR>
vnoremap <silent> <Left> :call MoveLeft()<CR>
nnoremap <silent> <Right> :call MoveRight()<CR>
inoremap <silent> <Right> <C-o>:call MoveRight()<CR>
snoremap <silent> <Right> :call MoveRight()<CR>
vnoremap <silent> <Right> :call MoveRight()<CR>

nnoremap <silent> e :call MoveUp()<CR>
snoremap <silent> e :call MoveUp()<CR>
vnoremap <silent> e :call MoveUp()<CR>
nnoremap <silent> <C-e> :call MoveUp()<CR>
inoremap <silent> <C-e> <C-o>:call MoveUp()<CR>
snoremap <silent> <C-e> :call MoveUp()<CR>
vnoremap <silent> <C-e> :call MoveUp()<CR>
nnoremap <silent> d :call MoveDown()<CR>
snoremap <silent> d :call MoveDown()<CR>
vnoremap <silent> d :call MoveDown()<CR>
nnoremap <silent> <C-d> :call MoveDown()<CR>
inoremap <silent> <C-d> <C-o>:call MoveDown()<CR>
snoremap <silent> <C-d> :call MoveDown()<CR>
vnoremap <silent> <C-d> :call MoveDown()<CR>
nnoremap <silent> s :call MoveLeft()<CR>
snoremap <silent> s :call MoveLeft()<CR>
vnoremap <silent> s :call MoveLeft()<CR>
nnoremap <silent> <C-s> :call MoveLeft()<CR>
inoremap <silent> <C-s> <C-o>:call MoveLeft()<CR>
snoremap <silent> <C-s> :call MoveLeft()<CR>
vnoremap <silent> <C-s> :call MoveLeft()<CR>
nnoremap <silent> f :call MoveRight()<CR>
snoremap <silent> f :call MoveRight()<CR>
vnoremap <silent> f :call MoveRight()<CR>
nnoremap <silent> <C-f> :call MoveRight()<CR>
inoremap <silent> <C-f> <C-o>:call MoveRight()<CR>
snoremap <silent> <C-f> :call MoveRight()<CR>
vnoremap <silent> <C-f> :call MoveRight()<CR>

nnoremap <silent> w ^
snoremap <silent> w ^
vnoremap <silent> w ^
nnoremap <silent> <C-w> ^
inoremap <silent> <C-w> <C-o>^
snoremap <silent> <C-w> ^
vnoremap <silent> <C-w> ^
nnoremap <silent> r $
snoremap <silent> r $
vnoremap <silent> r $
nnoremap <silent> <C-r> $
inoremap <silent> <C-r> <C-o>$
snoremap <silent> <C-r> $
vnoremap <silent> <C-r> $
nnoremap <silent> t gg
snoremap <silent> t gg
vnoremap <silent> t gg
nnoremap <silent> <C-t> gg
inoremap <silent> <C-t> <C-o>gg
snoremap <silent> <C-t> gg
vnoremap <silent> <C-t> gg
nnoremap <silent> g G
snoremap <silent> g G
vnoremap <silent> g G
nnoremap <silent> <C-g> G
inoremap <silent> <C-g> <C-o>G
snoremap <silent> <C-g> G
vnoremap <silent> <C-g> G

" 模式映射
nnoremap <silent> <F13> <Esc>a
snoremap <silent> <F13> <Esc>a
vnoremap <silent> <F13> <Esc>a
nnoremap <silent> <C-j> v
inoremap <silent> <C-j> <C-o>v
nnoremap <silent> <C-k> V
inoremap <silent> <C-k> <C-o>V
nnoremap <silent> <C-b> r

" 修改映射
nnoremap <silent> x d
snoremap <silent> x d
vnoremap <silent> x d
nnoremap <silent> <C-x> d
inoremap <silent> <C-x> <C-o>d
snoremap <silent> <C-x> d
vnoremap <silent> <C-x> d
nnoremap <silent> c y
snoremap <silent> c y
vnoremap <silent> c y
nnoremap <silent> <C-c> y
inoremap <silent> <C-c> <C-o>y
snoremap <silent> <C-c> y
vnoremap <silent> <C-c> y
nnoremap <silent> v p
snoremap <silent> v p
vnoremap <silent> v p
nnoremap <silent> <C-v> p
inoremap <silent> <C-v> <C-o>p
snoremap <silent> <C-v> p
vnoremap <silent> <C-v> p

nnoremap <silent> z u
snoremap <silent> z u
vnoremap <silent> z u
nnoremap <silent> <C-z> u
inoremap <silent> <C-z> <C-o>u
snoremap <silent> <C-z> u
vnoremap <silent> <C-z> u
nnoremap <silent> q .
snoremap <silent> q .
vnoremap <silent> q .
nnoremap <silent> <C-q> .
inoremap <silent> <C-q> <C-o>.
snoremap <silent> <C-q> .
vnoremap <silent> <C-q> .

" 搜索映射
nnoremap <silent> . n
snoremap <silent> . n
vnoremap <silent> . n
nnoremap <silent> <C-.> n
inoremap <silent> <C-.> <C-o>n
snoremap <silent> <C-.> n
vnoremap <silent> <C-.> n
nnoremap <silent> , N
snoremap <silent> , N
vnoremap <silent> , N
nnoremap <silent> <C-,> N
inoremap <silent> <C-,> <C-o>N
snoremap <silent> <C-,> N
vnoremap <silent> <C-,> N

" 命令映射
nnoremap <C-;> :
inoremap <C-;> <C-o>:

" 安装插件。
call plug#begin()

Plug 'Vim-airline/Vim-airline'

Plug 'Chiel92/Vim-autoformat'
let g:autoformat_verbosemode=0 " 详细模式。
let g:autoformat_autoindent = 0
let g:autoformat_retab = 1
let g:autoformat_remove_trailing_spaces = 1
let g:formatdef_hl_js='" js-beautify" '
let g:formatdef_hl_c='" clang-format -style=\" {BasedOnStyle: LLVM, UseTab: Never, IndentWidth: 4, PointerAlignment: Right, ColumnLimit: 150, SpacesBeforeTrailingComments: 1}\" " ' " 指定格式化的方式, 使用配置参数。
let g:formatters_c = ['hl_c']
let g:formatters_cpp = ['hl_c']
let g:formatters_json = ['hl_js']
let g:formatters_js = ['hl_js']
let g:formatdef_sqlformat = '" sqlformat --keywords upper -" '
let g:formatters_sql = ['sqlformat']
" 保存时自动格式化指定文件类型代码
" au BufWrite *:Autoformat
" autocmd BufWrite *.sql,*.c,*.py,*.java,*.js:Autoformat " 设置发生保存事件时执行格式化。

Plug 'Preservim/Nerdtree'
Plug 'Xuyuanp/Nerdtree-git-plugin' " 目录树 git 状态显示。
" 设置“<F1>”开启和关闭 NerdTree。
map <F1> :NERDTreeToggle<CR>
let NERDTreeChDirMode=1
let NERDTreeShowBookmarks=1 " 显示书签
let NERDTreeIgnore=['\~$', '\.pyc$', '\.swp$'] " 设置忽略文件类型。
let NERDTreeWinSize=25 " 窗口大小

Plug 'Mbbill/Undotree'
" 设置“<F2>”开启和关闭 Undotree。
map <F2> :UndotreeToggle<CR>

Plug 'Yggdroot/IndentLine'
let g:indentLine_enabled = 1  " 使插件生效。
let g:indentLine_char = '|'  " 设置缩进字符，可以是 '|', '┆', '┊' 等。
let g:indentLine_conceallevel = 2  " 使插件正常运行。

Plug 'Godlygeek/Tabular'

call plug#end()
```

## 操作

### 模式

1. 正常模式：我们进入 Vim 的时候就是正常模式。这种模式下可以使用相应命令进行操作。在任何其他模式下，按“\<Esc>”键，可以进入正常模式。
2. 插入模式：正常模式下，按“a”或“i”键，可以进入插入模式。在这种模式下，可以对文件进行编辑。这里我们在“\_vimrc”设置了“autocmd VimEnter * :startinsert”，则预设即为编辑模式。在“\_vimrc”设置后绑定为“\<Ctrl>＋\<ESC>”键，也能进入插入模式。
3. 命令模式：正常模式下，按“:”（小写冒号）键，可以进入插入模式。在命令模式中可以执行一些输入并执行一些 Vim 或插件提供的指令，就像在 shell 里一样。这里我们在“\_vimrc”设置后绑定为“\<Ctrl>＋:”键，也能进入命令模式。
4. 可视模式：正常模式下，按“v”键，可以进入可视模式，可以进行块选取。这里我们在“\_vimrc”设置后绑定为“\<Ctrl>＋j”键。正常模式下，按“V”键，可以进入可视行模式：即立即选取一行。这里我们在“\_vimrc”设置后绑定为“\<Ctrl>＋k”键。
5. 选择模式：用鼠标拖选区域的时候，就进入了选择模式。在这个模式下，选择完后，敲任何按键就直接输入并替换选择的文本了。
6. 替换模式：正常模式下，按“r”键，可以进入替换模式，进行单字替换，替换完后进入正常模式。正这里我们在“\_vimrc”设置后绑定为“\<Ctrl>＋b”键。常模式下，按“R”键，可以进入连续替换模式，进行连续替换。

### 快捷键

#### 移动 

| 键位           | 原键位 | 功能                           |
| ------------ | --- | ---------------------------- |
| s 或\<Ctrl>＋s | h   | 光标向左移动一次，5h 表示光标向左移动 5 次。    |
| d 或\<Ctrl>＋d | gj  | 光标向下移动一次，5gj 表示光标向下移动 5 次。   |
|              | j   | 光标向下移动一行。用 5j 表示光标向下移动 5 行。  |
| e 或\<Ctrl>＋e | gk  | 光标向上移动一次，用 5gk 表示光标向上移动 5 次。 |
|              | k   | 光标向上移动一行，用 5k 表示光标向上移动 5 行。  |
| f 或\<Ctrl>＋f | l   | 光标向右移动一次，用 5l 表示光标向右移动 5 次。  |
| w 或\<Ctrl>＋w | ^   | 光标移动到行首。                     |
| r 或\<Ctrl>＋r | $   | 光标移动到行尾。                     |
| t 或\<Ctrl>＋t | gg  | 光标移动到行首。                     |
| g 或\<Ctrl>＋g | G   | 光标移动到行尾。                     |
| a 或\<Ctrl>＋a |     | 全选。                          |
|              | H   | 光标移动到屏幕上部可见行的开头。             |
|              | M   | 光标移动到屏幕中间可见行的开头。             |
|              | L   | 光标移动到屏幕下部可见行的开头。             |
|              | %   | 光标在配对出现的符号时候，移动到另一侧。         |
| n 或\<Ctrl>＋n | w   | 跳转到下一个单词的开头。                 |
| m 或\<Ctrl>＋m | b   | 跳转到上一个单词的开头。                 |
|              | f＋x | 同一行内，向右跳转到第一个“x”。            |
|              | F＋x | 同一行内，向左跳转到第一个“x”。            |

#### 模式 

| 键位            | 原键位 | 功能                       |
| ---             | ---    | ---                        |
| \<ESC>          |        | 进入正常模式。             |
| i               | i      | 进入插入模式，在之前插入。 |
| \<Ctrl>＋\<ESC> | a      | 进入插入模式，在之后插入。 |
| \<Ctrl>＋j      | v      | 进入可视模式。             |
| \<Ctrl>＋k      | V      | 进入可视行模式。           |
| \<Ctrl>＋b      | r      | 进入替换模式。             |

#### 模式 

| 键位 | 原键位 | 功能                         |
| ---  | ---    | ---                          |
|      | a      | 光标所在的字符之后插入。     |
|      | i      | 光标所在的字符之前插入。     |
|      | A      | 光标所在行的行尾插入。       |
|      | I      | 光标所在的字符之前插入。     |
|      | o      | 光标所在行的下一行行首插入。 |
|      | O      | 光标所在行的上一行行首插入。 |

#### 修改 

| 键位           | 原键位 | 功能                                                |
| ---            | ---    | ---                                                 |
| x 或\<Ctrl>＋x | d      | 剪切，用 5d 表示剪切 5 个字符。                     |
| c 或\<Ctrl>＋c | y      | 复制，用 5y 表示复制 5 个字符。                     |
| v 或\<Ctrl>＋v | p      | 粘贴，用 5p 表示粘贴 5 个字符。                     |
|                | dd     | 剪切一行，用 5dd 表示剪切 5 行。                    |
|                | yy     | 复制一行，用 5yy 表示复制 5 行。                    |
|                | x      | 删除当前光标所在处的字符，用 5x 表示删除 5 个字符。 |
| z 或\<Ctrl>＋z | u      | 撤销上一步操作，用 5u 表示撤销 5 次。               |
| y 或\<Ctrl>＋y |        | 反撤销上一步操作。                                  |
| q 或\<Ctrl>＋q | .      | 重复上一步操作。                                    |
|                | cw     | 删除光标处一个单词，并进入插入模式。                |
|                | ci(    | 删除括号内的内容，并进入插入模式。                  |
|                | c^     | 删除至行首，并进入插入模式。                        |
|                | c$     | 删除至行尾，并进入插入模式。                        |

#### 搜索 

| 键位            | 原键位         | 功能                                |
| ---             | ---            | ---                                 |
| / 或\<Ctrl>＋/  |                | 查找。                              |
| h 或\<Ctrl>＋h  |                | 替换。                              |
|                 | /abc           | 向下搜索 abc 这个词一次。           |
|                 | ?abc           | 向上搜索 abc 这个词一次。           |
|                 | /\<abc>        | 向下精确匹配搜索 abc 这个词一次。   |
|                 | /\\t           | 向下搜索 \<Tab> 这个符号一次。      |
|                 | /\\s           | 向下搜索 \<Space> 这个符号一次。    |
| . 或\<Ctrl>＋.  | n              | 跳到下一个匹配项。                  |
| , 或\<Ctrl>＋,  | N              | 跳到上一个匹配项。                  |
|                 | *              | 向下搜索光标所在单词一次。          |
|                 | #              | 向上搜索光标所在单词一次。          |
|                 | :s/abc/def     | 行内替换 abc 为 def 一次。          |
|                 | :s/abc/def/g   | 行内替换所有 abc 为 def。           |
|                 | :%s/abc/def/g  | 全文替换 abc 为 def。               |
|                 | :%s/abc/def/gc | 全文替换 abc 为 def，要求每次确认。 |

#### 文件操作 

| 键位           | 原键位 | 功能             |
| ---            | ---    | ---              |
| : 或\<Ctrl>＋; | :      | 进入命令模式。   |
| :q             |        | 退出。           |
| :q!            |        | 强制不保存退出。 |
| :w             |        | 写入。           |
| :wq            |        | 保存并退出。     |
| :wq!           |        | 强制保存并退出。 |

![](./Vim.md.files/Vim%20Keyboard-layout.avif)

<!--
["Esc\n正常模式",{x:1},"F1","F2","F3","F4",{x:0.5},"F5","F6","F7","F8",{x:0.5},"F9","F10","F11","F12",{x:0.25},"PrtSc","Scroll Lock","Pause\nBreak"],
[{y:0.5},"~\n`","!\n1","@\n2","#\n3","$\n4","%\n5","^\n6","&\n7","*\n8","(\n9",")\n0","_\n-","+\n=",{w:2},"Backspace",{x:0.25},"Insert","Home","PgUp",{x:0.25},"Num Lock","/","*","-"],
[{w:1.5},"Tab","Q\n重复","W\n行首","E\n上移","R\n行尾","T\n全文首","Y\n反撤销","U","I\n插入模式","O","P","{\n[","}\n]",{w:1.5},"|\n\\",{x:0.25},"Delete","End","PgDn",{x:0.25},"7\nHome","8\n↑","9\nPgUp",{h:2},"+"],
[{w:1.75},"Caps Lock","A\n全选","S\n左移","D\n下移","F\n右移","G\n全文尾","H\n替换","J\n可视模式","K\n可视行模式","L",":\n; 命令模式","\"\n'",{w:2.25},"Enter",{x:3.5},"4\n←","5","6\n→"],
[{w:2.25},"Shift","Z\n撤销","X\n剪切","C\n复制","V\n粘贴","B\n替换模式","N\n下一个单词","M\n上一个单词","<\n, 上一个匹配",">\n. 下一个匹配","?\n/ 查找",{w:2.75},"Shift",{x:1.25},"↑",{x:1.25},"1\nEnd","2\n↓","3\nPgDn",{h:2},"Enter"],
[{w:1.25},"Ctrl",{w:1.25},"Win",{w:1.25},"Alt",{a:7,w:6.25},"",{a:4,w:1.25},"Alt",{w:1.25},"Win",{w:1.25},"Menu",{w:1.25},"Ctrl",{x:0.25},"←","↓","→",{x:0.25,w:2},"0\nIns",".\nDel"]
["Esc\n正常模式",{x:1},"F1","F2","F3","F4",{x:0.5},"F5","F6","F7","F8",{x:0.5},"F9","F10","F11","F12",{x:0.25},"PrtSc","Scroll Lock","Pause\nBreak"],
[{y:0.5},"~\n`","!\n1","@\n2","#\n3","$\n4","%\n5","^\n6","&\n7","*\n8","(\n9",")\n0","_\n-","+\n=",{w:2},"Backspace",{x:0.25},"Insert","Home","PgUp",{x:0.25},"Num Lock","/","*","-"],
[{w:1.5},"Tab","Q\n重复","W\n行首","E\n上移","R\n行尾","T\n全文首","Y\n反撤销","U","I\n插入模式","O","P","{\n[","}\n]",{w:1.5},"|\n\\",{x:0.25},"Delete","End","PgDn",{x:0.25},"7\nHome","8\n↑","9\nPgUp",{h:2},"+"],
[{w:1.75},"Caps Lock","A\n全选","S\n左移","D\n下移","F\n右移","G\n全文尾","H\n替换","J\n可视模式","K\n可视行模式","L",":\n; 命令模式","\"\n'",{w:2.25},"Enter",{x:3.5},"4\n←","5","6\n→"],
[{w:2.25},"Shift","Z\n撤销","X\n剪切","C\n复制","V\n粘贴","B\n替换模式","N\n下一个单词","M\n上一个单词","<\n, 上一个匹配",">\n. 下一个匹配","?\n/ 查找",{w:2.75},"Shift",{x:1.25},"↑",{x:1.25},"1\nEnd","2\n↓","3\nPgDn",{h:2},"Enter"],
[{w:1.25},"Ctrl",{w:1.25},"Win",{w:1.25},"Alt",{a:7,w:6.25},"",{a:4,w:1.25},"Alt",{w:1.25},"Win",{w:1.25},"Menu",{w:1.25},"Ctrl",{x:0.25},"←","↓","→",{x:0.25,w:2},"0\nIns",".\nDel"]
-->

## 插件

### Vim-plug

安装 vim-plug，下载 plug.vim 文件，放在安装文件夹下“vimfiles\autoload\”内。
https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
ed2k://|file|plug.vim|84862|0962D8DA52E133CC8AE92EC6D0928A41|h=Q5Q5ZLM4N37MIW332E4AOBAT2YLHIIH7|/

在“\_vimrc”文件内，添加内容：

```
call plug#begin()

Plug ' '

call plug#end()
```

其中 Plug ' '内是插件名，多个插件分行并列。

最后，启动 Vim，安装插件。

```
:PlugInstall    ; 安装所有插件
```

![](./Vim.md.files/PixPin_2025-04-16_05-14-39.avif)

插件的其他命令：

```
:PlugUpdate      " 更新所有插件
:PlugUpgrade    " 更新插件本身
:PlugClean        " 删除未标记的插件
```

### Vim-airline/Vim-airline

Vim-airline 插件用来在底部与顶部展示状态信息的。

![](./Vim.md.files/PixPin_2025-04-19_02-35-37.avif)

### Chiel92/Vim-autoformat

自动格式化管理插件，可根据不同文件类型使用不同的格式化工具。

### Preservim/Nerdtree 与 Xuyuanp/Nerdtree-git-plugin

这是 Vim 编辑器的文件系统浏览器。

![](./Vim.md.files/PixPin_2025-04-19_02-34-19.avif)

### Mbbill/Undotree

这是用来查看内容变更历史，以便于撤销或者重做的操作。

![](./Vim.md.files/PixPin_2025-04-19_02-34-45.avif)

### Yggdroot/IndentLine

这是用来在 vim 中提供缩进线标示功能的。

![](./Vim.md.files/PixPin_2025-04-19_02-38-33.avif)

### Godlygeek/Tabular

这是用来快速按照给定的分隔符号完成指定范围内的对齐插件。

```
:Tabularize /|/     ; 安装“|”对齐。
```
