# Linux Self-directed Learning

## 一.系统常见命命令

### 1.Linux系统命令提示符组成

```bash
[root@mosiy ~]#  
# root         Linux操作系统的管理员 显示当前登录的系统用户
# @            分隔符
# mosiy        主机名称
# ~            显示当前所在的路径(当前在哪个目录下)
# ~            表示家目录 /root/  默认登录操作系统所在的位置
#  $           表示用户的提示符  # 表示管理员用户   $表示普通用户
```

### 2.系统关机重启命令

 命令语法格式:

Linux命令      直接回车
Linux命令 空格 [参数选项]   # 每个参数表示不同的功能
Linux命令 空格 [参数选项] 空格 文件/目录
注意: 在Linux操作系统中[] 表示可选项 或者的含义

案例：

```bash
1.shutdown        #关机 
                  #直接回车 默认1分钟后关机
           -h     #参数选项
  shutdown -h 5   # 表示5分钟后关闭操作系统
  shutdown -h now # 表示立刻关机
           -c     # 取消关机
  shutdown -c     # 取消关机或者重启
2.poweroff        #直接回车 直接关机
3.init 0          #直接回车 直接关机
4.shutdown -r     #重启
           -r     #重启
  shutdown -r 5   # 5分钟后重启
  shutdown -r now # 立刻重启
5.reboot          #直接重启
6.init 6          #直接重启
```

### 3. 目录结构

绝对路径与相对路径：

绝对路径  例如：`[root@mosiy ~]# cd /etc/sysconfig/network-scripts/` 

相对路径  例如：`[root@mosiy ~]# cd /etc/sysconfig/
               [root@mosiy sysconfig]# cd network-scripts/`  

### 4.Linux操作系统命令

#### 1.pwd             #查看当前所在的路径 print working directory

    [root@mosiy ~]# pwd
    /root           # 默认的出生地在家里面/目录 root目录

#### 2.cd                 #切换目录  change directory

           Tip: Linux系统中目录结尾可以加/ 也可以不加
           如果使用tab键 出来的结果带/ 表示是一个目录  如果不带/ 表示是一个普通文件

#### 3.回到家目录(三种方法)

[root@mosiy ~]# cd ~

 [root@mosiy ~]# cd

[root@mosiy ~]# cd /root

#### 4.回到上一级目录（两种方法）

[root@mosiy mosssiy]# cd ..                #法一

[root@mosiy ~]# 

[root@mosiy mosssiy]# cd -                #法二
/root

#### 5.ls    #显示文件 查看文件或者目录是否存在   list

    -l  # 显示详细信息
    
    -a  # 显示隐藏的文件或目录     all所有

#### 6.touch   #创建普通文件 如果文件存在则只修改文件的时间 不会影响文件的内容

语法结构：

    touch file                   #在当前位置创建普通文件
    touch file1 file2 filen      #一次性创建多个文件
    touch /etc/NJZ               #在指定的目录下创建NJZ目录  
     也可以配合 .. 来使用：
      [root@mosiy NJZ]# touch ../mosssiy.txt
      
    注意: 在目录下创建普通文件，目录必须存在的，不支持递归创建
    touch test/test1/test2/a.txt  # test/test1/test2 三个目录必须存在


#### 7.mkdir   #创建目录  make directory

语法结构：

    mkdir 目录名称       # 创建单个目录
    mkdir dir1  dir2    # 创建多个目录
    mkdir /opt/目录名称   # 指定在某个目录下创建
                    -p   # 递归创建目录
                    
    example：[root@mosiy ~]# mkdir -p abc/111/222
             [root@mosiy ~]# ll abc/111/
             total 0
             drwxr-xr-x 2 root root 6 Jun 17 22:32 222

**注意: 创建目录可以递归，创建文件不可以递归**

#### 8.tree   #数型结构显示目录

            -L 1  #只显示1级目录
            -L 2  #只显示2级目录
    e.g.[root@mosiy ~]# tree -L 1
    .
    ├── abc
    ├── mosssiy.txt
    └── NJZ
    
    2 directories, 1 file
    [root@mosiy ~]# tree -L 2
    .
    ├── abc
    │   └── 111
    ├── mosssiy.txt
    └── NJZ
        └── NEWJEANS
    
    3 directories, 2 files

**容易出现的问题**

[root@mosiy ~]# tree

-bash: tree: command not found    #没有找到tree的命令，需要安装tree命令

*如何安装tree命令*

`yum -y install tree`>>>>>>>>>>>>#要求联网

*如何检查是否已经连接外网*>>>>>>>>>>>e.g.`ping www.baidu.com`

若ping的通  则连上了外网  *退出ping命令*>>>>>>>*使用Ctrl+C 强制退出*

#### 9.cat    #查看文件的内容，合并多个文件

        -n  # 显示行号 number

语法结构:
                cat 文件
                cat /目录/文件
                cat file1 file2 
案例1.查看/etc/hosts文件中的内容

`[root@mosiy ~]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6`

e.g.查看文件内容:*查看家目录下njz内容*

[root@mosiy ~]# cat njz.txt 
love

*若什么都不显示  则为空*

**配置文件存放的位置在：/etc/sysconfig/network-scripts/ifcfg-eth0**

也可以使用cat命令查看配置文件: e.g.cat  /etc/sysconfig/network-scripts/ifcfg-eth0

e.g.显示行号实际操作:

`[root@mosiy ~]# cat -n /etc/hosts
     1    127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
     2    ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6`

#### 10.clear   #清屏

### Linux中系统常用的快捷键

1.Ctrl+c            #强制结束当前的操作

2.Ctrl+l            #清屏

3.Ctrl+a           #快速移动光标到行首  Home键

4.Ctrl+e            #快速移动光标到行尾  End

5.Ctrl+← →     #移动一个单词

6.Ctrl+u            #剪切光标所在到行首

7.Ctrl+y            #粘贴剪切的内容
