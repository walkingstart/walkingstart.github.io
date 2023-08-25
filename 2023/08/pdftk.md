# Pdftk for pdf
25 August 2023

## fist install
    pkg_add pdftk

##  批量添加水印，report 文件夹下有多个 PDF，包括嵌套的文件夹，（准备好 sy.pdf 文件，运行命令，

>   find report -name '*.pdf' |while read f;do pdftk $f stamp sy.pdf output $f.pdf;mv $f.pdf $f;done;
##  下面示例：


>   合并 PDF：

>   pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf

>   或者 （使用通配符）:

>   pdftk *.pdf cat output combined.pdf

>   把多个 PDF 的不同页面组合成一个新的 PDF 文档（将 one.pdf 的前 7 页，two.pdf 的前 5 页，one.pdf 的第 8 页按先后顺序合并成 combined.pdf)

>   pdftk A=one.pdf B=two.pdf cat A1-7 B1-5 A8 output combined.pdf

>   旋转 PDF 的第一页为顺时针 90 度（向东）（其余页方向不变，2-end 表示第 2 页到最后一页）

>   pdftk in.pdf cat 1E 2-end output out.pdf

>   旋转 PDF 的第一页为逆时针（向西）90 度，只提取第一页

>   pdftk in.pdf cat 1W output out.pdf

>   选择所有 PDF 页面 180 度：

>   pdftk in.pdf cat 1-endS output out.pdf

>   使用 128 强度加密 PDF（安全模式，只读）

>   pdftk in.pdf output mydoc.128.pdf owner_pw foopass

>   同上，同时给 PDF 加上访问密码（会弹出一个密码输入框）

>   pdftk in.pdf output mydoc.128.pdf owner_pw foo user_pw baz

>   同上，但是运行打印：

>   pdftk in.pdf output mydoc.128.pdf owner_pw foo user_pw baz allow printing

>   解密 PDF 文档 (foopass 替换成 pdf 的 owner_pw 密码）：注意：前提是你得知道 pdf 的密码所以此功能只是解除所有者的密码，使阅读者不需要输密码

>   pdftk secured.pdf input_pw foopass output unsecured.pdf

>   合并两个 PDF 文档，其中一个是加密的，但最终文档不加密：

>   pdftk A=secured.pdf mydoc.pdf input_pw A=foopass cat output combined.pdf

>   解压 PDF 流，以便文本编辑：（不清楚是干什么用的）

>   pdftk mydoc.pdf output mydoc.clear.pdf uncompress

>   压缩 PDF：

>   pdftk mydoc.pdf output mydoc.clear.pdf compress

>   修复 PDF 文档

>   pdftk broken.pdf output fixed.pdf

>   分解成单页（文件名以 pg_开头）

>   pdftk mydoc.pdf burst

>   报告 PDF 信息，输出到文本

>   pdftk mydoc.pdf dump_data output report.txt
