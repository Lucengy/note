# Shell 笔记

## ctrl

* ctrl+a 光标到行首
* ctrl+e 光标到行尾
* ctrl+箭头 光标跨单词
* ctrl+w 删除光标所在单词
* ctrl+r 历史搜索
* ctrl+L 清屏
* ctrl+u 删除光标前所有内容
* ctrl+k 删除光标后所有内容

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
* awk '{printf("%s\t%s\t%s\t%s\n", $10, $11, $12, $13)}' /tmp/1.txt  按要求输出10-13列，分隔符为\t，末尾加换行符

## cat

* cat -n file 显示行号
* cat -A file 可以显示所有内容，包括换行符，主要用来查找文件中莫名其妙的空格和指标符

## tar

* tar czvf abc.tgz abc     将文件abc打包压缩为abc.tgz
* tar xzvf abc.tgz            解压缩abc.tgz
* xzvf针对的文件后缀为.tgz或者.tar.gz，针对.tar文件，使用tar xvf进行解压

## tr

* cat 1.txt | tr 'a-z' 'A-Z' 	将1.txt内容中的小写转换为大写
* cat 1.txt | tr -s 'a-z'         将1.txt内容中的连续字母去重

### head

* head -10 file1.txt 打印文件file1.txt的前10行
* head -c 10 file1.txt 打印文件file1.txt的前10个字节
* head -c -10 file1.txt 打印文件file1.txt除去最后10个字节的内容