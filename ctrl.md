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

* awk '{print NF}' file 显示文件有多少列

  由此引申，awk '{print $NF}' file 打印文件的最后一列

  ​				  awk '{print $(NF-1)}' file 打印文件的倒数第二列

* awk -F'split' file '{print $1}' 按split分割文件file，输出第1列

* cat file | awk '$1=="abc"' '{print $0}' 当文件file中的第1行值为abc时，输出整行

* awk -v OFS='\t' '{print $10,$11,$12,$13}' /tmp/1.txt  按要求输出10-13列，分隔符为\t，末尾加换行符

* 高级用法

  1. awk可以指定多个分隔符，使用|作为连接符

     案例: [[:space:]]代表空格，[[:space]]+代表一个以上的空格

     ```shell
     # df -h
     Filesystem           Size  Used Avail Use% Mounted on
     devtmpfs             3.8G     0  3.8G   0% /dev
     tmpfs                3.8G     0  3.8G   0% /dev/shm
     tmpfs                3.8G  9.1M  3.8G   1% /run
     tmpfs                3.8G     0  3.8G   0% /sys/fs/cgroup
     /dev/mapper/cs-root   69G  5.2G   64G   8% /
     /dev/nvme0n1p1      1014M  234M  781M  24% /boot
     tmpfs                767M     0  767M   0% /run/user/0
     
     # df -h |awk -F'[[:space:]]+|%' '{print $1,$5}'
     Filesystem Use
     devtmpfs 0
     tmpfs 0
     tmpfs 1
     tmpfs 0
     /dev/mapper/cs-root 8
     /dev/nvme0n1p1 24
     tmpfs 0
     
     # 下面这条命令跟上面是类似的意思，使用空格或者%作为分隔符。但是这里只有一个空格
     # df -h |awk -F'[ %]' '{print $1,$5}'
     ```

## cat

* cat -n file 显示行号
* cat -A file 可以显示所有内容，包括换行符，主要用来查找文件中莫名其妙的空格和指标符

## tar

* tar czvf abc.tgz abc     将文件abc打包压缩为abc.tgz
* tar xzvf abc.tgz            解压缩abc.tgz
* xzvf针对的文件后缀为.tgz或者.tar.gz，针对.tar文件，使用tar xvf进行解压
* 高版本的tar软件，会识别压缩格式，可以统一使用xvf进行解压

## tr

* cat 1.txt | tr 'a-z' 'A-Z' 	将1.txt内容中的小写转换为大写
* cat 1.txt | tr -s 'a-z'         将1.txt内容中的连续字母去重

## head

* head -10 file1.txt 打印文件file1.txt的前10行
* head -c 10 file1.txt 打印文件file1.txt的前10个字节
* head -c -10 file1.txt 打印文件file1.txt除去最后10个字节的内容

## vim

![1752797606571](C:\Users\v587\AppData\Roaming\Typora\typora-user-images\1752797606571.png)

* 命令模式-->插入模式

  i insert, 在光标所在处输入

  I, 在光标所在行行首输入

  a append, 在光标后一个字符输入

  A, 在光标所在行行尾输入

  o, 在光标所在行下新建一行输入

  O, 在光标所在行上新建一行输入

1. 复制粘贴

   ```shell
   :r filename # 将filename中的内容复制到光标处
   :w filename # 将当前文件内容写到filename中
   ```

2. vim中执行命令

   ```shell
   :!cmd # 敲击回车返回到vim
   ```

## bash

1. 检查脚本语法问题

   ```shell
   bash -n test.sh
   ```

2. debug模式

   ```shell
   bash -x test.sh
   ```

















































