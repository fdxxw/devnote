<!-- MarkdownTOC -->

- [1. 常用命令](#1-常用命令)
    - [1.1 查看进程](#11-查看进程)
    - [1.2 查看并重置代理](#12-查看并重置代理)
    - [1.3 备份还原](#13-备份还原)
    - [1.4 挂载](#14-挂载)
    - [1.5 查看分区UUID](#15-查看分区UUID)
    - [1.6 rsync ssh远程数据同步](#16-rsync-ssh远程数据同步)
    - [1.7 开放端口](#17-开放端口)
    - [1.8 查看当前目录下所有文件和目录的大小](#18-查看当前目录下所有文件和目录的大小)
- [2. 软件设置](#2-软件设置)
    - [2.1 vim](#21-vim)
    - [2.2 delete bom](#22-delete-bom)
    - [2.3 ssh](#23-ssh)
    - [2.3.1 ssh 配置文件路径](#231-ssh-配置文件路径)

<!-- /MarkdownTOC -->

#### 1. 常用命令
##### 1.1 查看进程
```
$ ps -ef | grep tomcat  #查看某个应用程序的进程信息
$ ps -aux

```
##### 1.2 查看并重置代理
```
$ env | grep proxy　　#查看代理

no_proxy=localhost,127.0.0.0/8,::1
https_proxy=http://127.0.0.1:46447/
http_proxy=http://127.0.0.1:46447/

$ unset https_proxy #重置代理
```

##### 1.3 备份还原
```sh
tar -jpcvf home.`date +%Y-%m-%d`.tar.bz2 --exclude-from=/backup/tar_exclude.list /home

tar -jpxvf home%.tar.bz2 -C /home

blkid #查看分区UUID
```

##### 1.4 挂载
```sh
curlftpfs 192.168.13.101 /mnt/ftp/ -o user=xingxiaowen:123456,allow_other,ftp_port=-

sshfs -p 22 root@192.168.1.1:/ /mnt/server

```
##### 1.5 查看分区UUID

```
blkid
```

##### 1.6 rsync ssh远程数据同步
```sh
rsync -Pv -e 'ssh -p 2000' root@111.111.111.111:/backup.tar.gz ./backup.tar.gz
```
##### 1.7 开放端口
```
iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 580 -j ACCEPT

```
[iptables](http://blog.csdn.net/luka2008/article/details/40391451)

##### 1.8 查看当前目录下所有文件和目录的大小
```sh
du * --block-size=M
```

#### 2. 软件设置
##### 2.1 vim 
缩进：在用户主目录下的.vimrc文件中加上一下代码
```
set tabstop=4 "tab 显示空格长度 默认为8
set softtabstop=4 "退格键退回的长度
set shiftwidth=4 "每一级缩进的长度
set expandtab "expandtab --缩进用空格来表示 noexpandtab --缩进用制表符来缩进
```

字符串替换
:%s#127.0.0.1:80#192.168.1.1:8080

##### 2.2 delete bom 
```sh
find . -type f   -exec  sed -i 's/\xEF\xBB\xBF//' {} \
```

##### 2.3 ssh

##### 2.3.1 ssh 配置文件路径
```
/etc/ssh/
```