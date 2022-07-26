# Linux

## 1 目录结构

 - **/bin** 常用命令，存放最经常使用的命令
 - **/home** 用户目录
 - **/root** 管理员目录
 - **/etc** 用户自己安装的应用程序的配置文件
 - **/usr** 安装程序默认文件夹，类似program files
 - **/mnt** 挂在别的文件系统，可以和windows互通
 - **/opt** 软件安装包目录
 - **/usr/local** 软件安装目录
 - **/var** 放经常会变化的文件，如日志文件
 - /sbin 管理员使用的系统管理程序
 - /lib 动态链接共享库
 - /lost+found 非法关机后，才存放文件
 - /boot linux启动的相关文件
 - /proc 虚拟目录，系统内存的映射，用来获取系统信息
 - /src 存放一些服务启动后需要提取的数据
 - /sys 与系统有关的文件
 - /tmp 存放临时文件
 - /dev 设备管理器，硬件设备以文件的形式存储
 - /media 自动识别设备，U盘、光驱等识别后挂载在此目录下
 - /selinux 安全子系统

## 2 vim的使用
vim与windows中的txt文件类似

基本操作有：创建并打开文件`vim hello.py`；进入编辑模式编辑文件`i,o,r`；退出编辑模式：`Esc`加上`:`同时输入`wq、q、q!`分别表示写入并退出、退出、强制退出；命令行模式键入`/或:`退出命令行`Esc`

一般模式快捷操作：

拷贝：yy，拷贝多行5yy，粘贴时输入p

删除：dd，删除多行5dd

查找：`:`进入命令行模式，`/关键字`搜索，回车后键入`n`滚动到下一个

设置文件行号：`:`进入命令行模式，输入`set nu`，取消行号，键入`set noun`

回到文件首尾行：一般模式下键入`G`跳转到末行，键入`gg`跳转到首行

撤销动作类似wins ctrl+z：按`Esc`回到一般模式，键入`u`

跳转指定行：一般模式下键入数字`x`，再按`shift+g`

## 3 关机重启和登录注销
关机重启：

`shutdown -h now`：立刻关机

`shutdown -h 1`：1分钟后关机

`shutdown -r now`：立刻重启

`halt`：和shutdown一样关机

`reboot`：立刻重启

`sync`：将数据同步磁盘

登录注销(在运行级别3下有用)：

`su - 用户名`：登录指定用户

`logout`：注销当前用户

## 4 级别切换和用户管理
### 4.1 级别切换
linux中共包含6个级别如下：

0：关机

1：单用户【找回丢失密码】

2：多用户状态没有网络

3：多用户状态连接网络

4：系统未使用保留用户

5：图形界面

6：系统重启

使用`init 0~6`指令切换图形界面

### 4.2 用户管理
用户创建：`useradd [name]`；`useradd -d /home/name jack`在指定路径下创建用户

修改密码：`passwd [name]`

用户删除：`userdel [name]`；同时删除用户文件`userdel -r [name]`

(`id`显示当前用户的id，`whoami`显示登录时的用户)

创建组：`groupadd 组名`；

删除组：`groupdel 组名`；

将用户加入组：`usrmod -g 组名 用户名`；

`usermod -d 目录名 用户名`：改变该用户登录的初始目录。（ps：用户需要有进入到新目录的权限）

## 5 帮助指令
### 5.1 man获取帮助信息

基本语法：`man 命令名或配置文件`

案例：查看ls命令的帮助信息 `man ls` 

linux下.开头的文件为隐藏文件 `ls -la /home`

### 5.2 help指令

## 6 文件目录指令
### 6.1 pwd 指令
print working directory 显示当前目录的绝对路径
### 6.2 ls 查看指令

基本语法：`ls [选项] 目录或文件`

常用选项：

-a ： 显示当前的目录的所有文件，包括隐藏文件

-l ： 以列表的形式显示信息

### 6.2 cd 指令
基本语法：`cd [参数] 路径`
`cd ~`: 回到家目录； `cd ..`：回到当前目录的上级目录
### 6.3 mkdir 指令
mkdir = make directory 用于创建目录 

基本用法：`mkdir [选项] 要创建目录`

常用选项：`-p`创建多级目录

### 6.4 rmdir 指令
rmdir = remove directory 删除**空目录**

基本语法：`rmdir [选项] 要删除的空目录`

如果要删除非空目录使用：`rm -rf 要删除的目录`，`r`表示递归，`f`表示强制 
### 6.5 touch 指令
touch指令用于创建空文件

基本语法：`touch 文件名称`
### 6.6 cp 指令
copy文件到指定目录

基本操作：`cp [选项] 文件路径 拷贝路径`

常用选项：`-r`：递归复制整个目录文件夹（包含多个目录）

强制覆盖不提示拷贝：`\cp`
### 6.7 rm 指令
rm指令用于移除文件或目录

基本语法：`rm [选项] 移除的文件`

常用选项：`-r`递归删除整个文件夹；`-f`强制删除不提示

### 6.8 mv 指令
移动文件或者目录重命名

基本语法：

重命名：`mv 旧名 新名` （同一个目录）

移动文件：`mv 旧路径 新路径`

### 6.9 cat 指令
用于查看文件内容

基本语法：`cat [选项] 要查看的文件`

常用选项：`-n`显示行号

为了浏览方便，一般会加上管道命令`|more`（Enter下一行，space下一页，q退出）
### 6.10 more 指令
用于查看文件内容

基本语法：`more 要查看的文件路径`
### 6.11 less 指令
用于分屏查看内容，用该指令查看时，并不是一次将整个文件加载后查看，而是根据需要查看的内容显示。

基本语法：`less 要查看的内容`
### 6.12 echo 指令
终端输出指令

基本语法：`echo "hello world!"`
### 6.13 head 指令
用于显示文件开头部分内容，默认前10行

基本语法：`head 想要查看的文件`；`head -n 5 文件`
### 6.14 tail 指令
用于输出文件尾部部分内容，默认情况下10行

基本语法：`tail 文件`；`tail -n 5 文件`
`tail -f 文件`用于追踪文件更新
### 6.15 > 和 >> 指令
\> 表示输出重定向，>> 表示追加

基本语法：

`ls -l > 文件` （列表内容写入到文件）

`ls -al >> 文件` （列表的内容追加到文件中）
### 6.16 ln 指令
ln 指令用于创建软连接，类似windows中的快捷方式，主要存放了连接其他文件的路径

基本语法：`ln -s 源文件 软链接名`
### 6.17 history 指令
用于查看历史指令

基本用法：`history`；`history 10`（查看10条）

`!n`调用用过的第n条指令
## 7 时间日期类指令
### 7.1 date指令-显示当前日期
基本语法：

1）`date`   显示当前时间

2）`date +%Y`   显示当前年份

3）`date +%m`   显示当前月份

4）`date +%d`   显示当前是哪一天

5）`date "+%Y-%m-%d %H:%M:%S"`  显示年月日时分秒
### 7.2 date指令-设置日期
基本语法：

`date -s "2020-11-03 20:02:11"`
### 7.2 cal 指令
查看日历指令

基本语法：`cal [选项]`；`cal 2020`
## 8 搜索查找类指令
### 8.1 find 指令
从指定目录下递归地遍历其各个子目录，将满足条件的文件或者目录显示在终端

基本语法：

`find 搜索范围 选项`

常用选项：

`-name<查询方式>`：按照指定的文件名查找模型查找文件

`-user<用户名>`：查找属于指定用户名所有文件名

`-size<文件大小>`：按照指定的文件大小查找文件
### 8.2 grep命令
基本语法：

`grep 选项 查找内容 源文件`

常用选项：

`-n`显示匹配行以及行行号

`-i`忽略字母大小写

## 9 解压与解压类
### 9.1 gzip/gunzip指令
gzip 用于压缩文件，gunzip用于解压

基本用法：

`gizp 文件` 只能将文件亚索为*.gz文件

`gunzip 文件.gz` 解压缩gz文件
### 9.2 zip/unzip 指令
zip用于压缩文件，unip用于解压

基本语法：

`zip 选项 XXX.zip` 将要压缩的内容

`unzip 选项 XXX.zip` 解压缩zip文件

常用选项：`-r`递归压缩，即压缩目录
### 9.3 tar 指令
打包指令，打包后的文件是.tar.gz后缀文件

基本语法：

`tar 选项 xxx.tar.gz 打包的内容`

选项说明：

`-c` 产生.tar 的打包文件

`-v` 显示详细信息

`-f` 指定压缩后的文件名

`-z` 打包同时压缩

`-x` 解包压缩文件

## 10 用户组
### 10.1 查看及修改文件所有者
查看：`ls -ahl`

修改：`chown 用户名 文件名`

例：使用root创建文件apple.txt，将其所有者改为tom

文件更改组名：

基本命令：`chgrp 组名 文件名`

## 11 rwx 权限
`ls -l`显示的内容如下：

-rwxrw-r-- 1 root root 1213 Feb 2 09：39 abc

xxxxxxxxxx

(前十位)

0-9 位说明
1. 第0位确定文件类型（d,-,l,c,b）
   
    l是连接，相当于Windows的快捷方式

    d是目录，相当于Windows的文件夹

    c是字符设备，鼠标，键盘
    
    b是块设备，比如硬盘
2. 第1-3位确定所有者（该文件的所有者）拥有该文件的权限。 --User
3. 第4-6位确定所属组（同用户组的）拥有该文件的权限 --Group
4. 第7-9位确定其他用户拥有该文件的权限 --Other