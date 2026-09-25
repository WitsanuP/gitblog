# old school way 
## req
- must haave `pdflatex` 
## let start
- creat file .tex
- pdflatex document.tex
- open .pdf


# workflow  way
## req
- neovim and plugin (vimtex)
- pdflatex // compiler
- latexmk  
- zathura // pdf viewer


## setup
### 1 install this 
```
sudo apt update
sudo apt install neovim
sudo apt install texlive-full
sudo apt install zathura
```


### 2 in this file`~/.config/nvim/init.vim`
```
" ===== เริ่มส่วนของ vim-plug =====
call plug#begin('~/.vim/plugged')

Plug 'lervag/vimtex'

call plug#end()
" ===== จบส่วนของ vim-plug =====

" ----- ตั้งค่า vimtex -----
let g:tex_flavor = 'latex'
let g:vimtex_view_method = 'zathura'
let g:vimtex_compiler_method = 'latexmk'

" ----- ตั้งค่าทั่วไปที่มีประโยชน์ -----
syntax on
set number
```
### 3 setup plugin neovim
install vim manage plugin
```
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
open neovim `nvim` 
```
:PlugInstall
```


## let start

command | meaning
--- | ---
\ll | compile(continuous compile - will compile when save file)
\lv | open pdf with zathura
\lc | clean file auxiliary (.aux, .log, other)
\lk | stop compile 


