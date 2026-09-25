using neovim and 

pdflatex --version  # compiler
latexmk --version   # auto compile
zathura --version   # pdf viewer

curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim


# old school way 
## req
- must haave `pdflatex` 
## let start
- creat file .tex
- pdflatex document.tex
- open .pdf


# work flow  way
## req
- neovim
- pdflatex // compiler
- latexmk  
- zathura // pdf viewer

neovim and plugin

## setup
```
sudo apt update
sudo apt install neovim
sudo apt install texlive-full
sudo apt install zathura
```


in this file`~/.config/nvim/init.vim`
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

## let start
