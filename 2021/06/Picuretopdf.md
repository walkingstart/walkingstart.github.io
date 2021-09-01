#   Picture to pdf
4   June 2021

pkg_add ImageMagick

    1. multi pictures to pdf 
    
>   ls input*.png | sort -n | tr '\n' ' ' | sed 's/$/\ output.pdf/' | xargs convert

    2.  combine pdf

>   convert pdf1.pdf pdf2.pdf temp.pdf

