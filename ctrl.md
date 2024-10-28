# Shell 笔记

## ctrl

* ctrl+a 光标到行首
* ctrl+e 光标到行尾
* ctrl+箭头 光标跨单词
* ctrl+w 删除光标所在单词

## 正则表达式

* ^pattern	以pattern开头

* pattern$	以pattern结尾

## sed

* sed -e 's/old/new/g' 	将old替换为new，不改变原文件，结果输出到屏幕
* sed -i 's/old/new/g'       将old替换为new，改变原文件
* sed -i '/^$/d'                删除空行

## awk

* awk 'NR=10000' file 显示文件的第10000行
* awk -F'split' file '{print $1}' 按split分割文件file，输出第1列
* cat file | awk '$1=="abc"' '{print $0}' 当文件file中的第1行值为abc时，输出整行

## cat

* cat -n file 显示行号

## tar

* tar czvf abc.tgz abc     将文件abc打包压缩为abc.tgz
* tar xzvf abc.tgz            解压缩abc.tgz
* xzvf针对的文件后缀为.tgz或者.tar.gz，针对.tar文件，使用tar xvf进行解压