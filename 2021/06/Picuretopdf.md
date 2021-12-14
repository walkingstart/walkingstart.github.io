#   Picture to pdf
4   June 2021

##  first install ImageMagick

    pkg_add ImageMagick

##  multi pictures to pdf

    ls input*.png | sort -n | tr '\n' ' ' | sed 's/$/\ output.pdf/' | xargs convert

    convert `ls  *.jpg | sort -n` foobar.pdf

##  combine pdf

    pdfunite pdf1.pdf pdf2.pdf temp.pdf

## rotate pdf
    qpdf --rotate=90 input.pdf output.pdf

