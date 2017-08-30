# Vim and Tmux configuration
 - [Vim Config](#vim-config)
   * [Update to Vim 8](#update-to-vim-8)
   * [Plugin Notes](#plugin-notes)
 - [Tmux Config](#tmux-config)
 - [How to cooperate vim and tmux](#how-to-cooperate-vim-and-tmux)
 - [SecureCRT configuration](#securecrt-configuration)
![Example Image](example.png)

## Vim Config
My vimrc and some candidates
- [`.vimrc`](.vimrc)
- https://github.com/samlaudev/ConfigurationFiles
- https://github.com/GoYchen/VIM_TMUX
- https://github.com/PytLab/dotfiles
- Reference: http://www.jianshu.com/p/f0513d18742a

[**HERE**](http://learnvimscriptthehardway.stevelosh.com/chapters/01.html) is a perfect book for you to learn vim scripts.

### Update to Vim 8
Vim 8 supports some convenient plugin. Update to vim 8 with the following lines.
```
sudo add-apt-repository ppa:jonathonf/vim     # get the newest version of vim
sudo apt-get update vim && sudo apt-get upgrade vim  # update package
sudo apt-get install vim-nox                  # add python3 support
```
To work with python 2
```
sudo apt install vim-nox-py2
sudo update-alternatives --set vim /usr/bin/vim.nox-py2
sudo update-alternatives --set vi /usr/bin/vim.nox-py2
```
### Plugin Notes
Plugin List

Name    | Function
----    | ---
'vim-airline/vim-airline'          | Status bar
'vim-airline/vim-airline-themes'   | Airline Themes 
'vim-scripts/wombat256.vim'        | Color Theme
'Valloric/YouCompleteMe'           | Autocomplete
'ctrlpvim/ctrlp.vim'               | File Search
'scrooloose/nerdtree'              | File Tree
'majutsushi/tagbar'                | Function and Variable Tag Bar
'Yggdroot/indentLine'              | show indent 
'jiangmiao/auto-pair'              | Auto pair ({["
'tpope/vim-surround'               | Add, delete, change delimiters 
'tell-k/vim-autopep8'              | F8 Auto format python file 
'scrooloose/nerdcommenter'         | F5 Quick comment 
'tpope/vim-fugitive'               | Git command in vim
'terryma/vim-smooth-scroll'        | Smooth scroll 
'godlygeek/tabular'                | Markdown 
'plasticboy/vim-markdown'          | Markdown

Get `Vundle` first by
```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```
Then install these Plugins by `:PluginInstall` in Vim.

#### YouCompleteMe
Ultimate auto-complete plugin for Vim. After installation, you need to compile it
```
cd ~/.vim/bundle/YouCompleteMe
./install.py --clang-completer
```
You also need to modify the following path in `.vimrc`
```
let g:ycm_global_ycm_extra_conf = "/home/cfchen/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py"
let g:ycm_server_python_interpreter= "/home/cfchen/anaconda2/bin/python2.7" 
```

#### Vim airline

Please make sure your terminal supports `utf-8`. Otherwise, airline symbol may not show properly.
If you don't want the fancy symbols, just modify the following airline symbols to any character you want in `.vimrc`.
```
let g:airline_left_sep = '⮀'
let g:airline_left_alt_sep = '⮁'
let g:airline_right_sep = '⮂'
let g:airline_right_alt_sep = '⮃'
let g:airline_symbols.crypt = '🔒'
let g:airline_symbols.linenr = '☰'
let g:airline_symbols.linenr = '␊'
let g:airline_symbols.linenr = '␤'
let g:airline_symbols.linenr = '¶'
let g:airline_symbols.maxlinenr = ''
let g:airline_symbols.maxlinenr = '㏑'
let g:airline_symbols.branch = '⎇'
let g:airline_symbols.paste = 'ρ'
let g:airline_symbols.paste = 'Þ'
let g:airline_symbols.paste = '∥'
let g:airline_symbols.spell = 'Ꞩ'
let g:airline_symbols.notexists = '∄'
let g:airline_symbols.whitespace = 'Ξ'
```

#### Other Custom Settings
*Normal Mode*
- F3, NerdTree; F4, Tagbar; F6, NerdTree and Tagbar
- F2, save and exit; Shift+s, save; Shift+q, exit

*Insert Mode*
- Ctrl+l, ESC

## Tmux Config

My tmux configuration is in [`.tmux.conf`](.tmux.conf)  
Main features are
- Rebind `Ctrl+b` to `Ctrl+x`
- Enable mouse to select window and panel, resize panel
- Enlarge history to 10000 lines
- Horizontal split: `bind-key s`, Vertical split: `bind-key v`
- Date and Time on status bar.

## How to cooperate vim and tmux 
For unknow reason, vim colortheme may not work in tmux without the following configuration  
(1) In .vimrc
```
se t_Co=256
set term=screen-256color
```
(2) In .bashrc
```
 alias tmux="TERM=screen-256color tmux" 
```
Note: please use `source ~/.bashrc` to make it effective.

## SecureCRT configuration
Remember keys in Mac. If you want to remember ssh keys in mac, you must turn off the key chains in `Preferences -> General -> Mac options`
### Color 
1. Change the theme to White/Black in `Preferences -> General -> Default Session -> Edit Default Settings -> Appearance`
1. You can also config the ANSI color under the `Appearance`, details see [this blog](http://liam0205.me/2015/09/24/color-scheme-for-securecrt/index.html)
### Session Setting
1. Hide tool bar, `Preferences -> General -> view`
1. Show path in tab, `Preferences -> General -> Default Session -> Edit Default Settings -> Terminal -> Emulation`.  
Change terminal to `Xterm`, tick `ANSI color`. Change to a bigger `Scroll back buffer` if you want. (Reference [blog](http://blog.csdn.net/delphiwcdj/article/details/7226921)) 
1. Enable `Fn` keys in Mac. Change terminal to `Xterm`.
