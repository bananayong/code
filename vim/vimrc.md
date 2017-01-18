#VIM config files

```
set nocompatible
filetype off

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

Plugin 'VundleVim/Vundle.vim'

" language
Plugin 'scrooloose/syntastic'
Plugin 'pangloss/vim-javascript'
Plugin 'tpope/vim-markdown'
Plugin 'tpope/vim-sensible'
Plugin 'othree/html5.vim'
Plugin 'elzr/vim-json'
Plugin 'klen/python-mode'
Plugin 'chase/vim-ansible-yaml'
Plugin 'ap/vim-css-color'
Plugin 'stephpy/vim-yaml'
Plugin 'zsh-users/zsh-syntax-highlighting'
Plugin 'zsh-users/zsh-completions'
Plugin 'zsh-users/zsh-history-substring-search'
Plugin 'robbles/logstash.vim'

" completeion
Plugin 'tpope/vim-surround'
Plugin 'valloric/youcompleteme'
Plugin 'ervandew/supertab'
Plugin 'sirver/ultisnips'
Plugin 'raimondi/delimitmate'
Plugin 'tpope/vim-endwise'
Plugin 'jiangmiao/auto-pairs'
Plugin 'townk/vim-autoclose'
Plugin 'AutoComplPop'
Plugin 'tpope/vim-repeat'
Plugin 'taglist.vim'

Plugin 'MarcWeber/vim-addon-mw-utils'
Plugin 'tomtom/tlib_vim'
Plugin 'garbas/vim-snipmate'
Plugin 'honza/vim-snippets'

" tools
Plugin 'scrooloose/nerdtree'
Plugin 'scrooloose/nerdcommenter'
Plugin 'xuyuanp/nerdtree-git-plugin'
Plugin 'kien/ctrlp.vim'
Plugin 'nathanaelkane/vim-indent-guides'
Plugin 'yggdroot/indentline'
Plugin 'kien/rainbow_parentheses.vim'
Plugin 'bronson/vim-trailing-whitespace'
Plugin 'majutsushi/tagbar'
Plugin 'godlygeek/tabular'
Plugin 'xolox/vim-misc'

" theme
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'
Plugin 'dracula/vim'
Plugin 'altercation/vim-colors-solarized'

" git
Plugin 'airblade/vim-gitgutter'
Plugin 'tpope/vim-fugitive'
Plugin 'tpope/vim-git'


call vundle#end()
filetype plugin indent on

syntax on

set number
set termencoding=utf-8
set encoding=utf-8

set laststatus=2
set cmdheight=2

set hidden

set wildmenu
set wildmode=list:full

set nocindent
set textwidth=79

set smartindent
set tabstop=4
set shiftwidth=4
set expandtab
set softtabstop=4

set nowrap
set backspace=indent,eol,start
set copyindent
set shiftround
set showmatch
set hlsearch
set incsearch

set history=1000
set undolevels=1000
set wildignore=*.swp,*.bak,*.pyc,*.class
set title
set visualbell
set nobackup
set noswapfile

autocmd filetype python set expandtab
autocmd filetype html setlocal ts=2 sts=2 sw=2 expandtab
autocmd filetype ruby setlocal ts=2 sts=2 sw=2 expandtab
autocmd filetype javascript setlocal ts=2 sts=2 sw=2 expandtab
autocmd filetype yml setlocal ts=2 sts2= sw=2 expandtab


let g:AutoPairsFlyMode = 1
let g:airline#extensions#tabline#enabled = 1
let g:airline_powerline_fonts = 1
set laststatus=2

set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0


" THEME
let g:solarized_termcolors=256
syntax enable
set background=dark
colorscheme solarized


let &t_Co=256
"set background=dark
let g:airline_theme='dracula'
"let g:airline_theme='base16_solarized'
"let g:airline_theme='dracula'


let g:AutoPairsFlyMode = 1
```
