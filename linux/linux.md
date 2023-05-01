# Linux

## vim

### vim的三种模式

- 正常模式

以vim打开一个档案就直接进入一般模式了(这是默认的模式)。在这个模式中，你可以使用【上下左右】按键来移动光标，你可以使用【删除字符】或【删除整行】来处理档案内容，也可以使用【复制、粘贴】来处理你的文件数据。

- 插入模式

按下``` i,I,o,O,a,A,r,R```等任何一个字母之后才会进入编辑模式，一般来说按`i`即可

- 命令行模式

先输入ESC退出 再输入:进入命令行模式

在这个模式当中，可以提供你相关指令，完成读取，存盘，替换、离开vim、显示行号等的动作则是在此模式中达成的！

### vim快捷键

> :wq(保存并退出)
>
> :q(退出)
>
> :q!(强制退出，不保存)

- 快捷键使用练习(以下操作需要在一般模式下才能使用 编辑模式无效)

![image-20230418172145764](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230418172145764.png)

<img src="C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230418174219496.png" alt="image-20230418174219496" style="zoom:80%;" />

## 用户管理

### 关机&重启命令

- 基本介绍

`shutdown -h now` 立刻进行挂机

`shutdown -h 1`  1minutes后关机

`shutdown -r now`  现在重启计算机

`halt`  关机

`reboot`  现在重启计算机

`sync`  把内存的数据同步到磁盘

- 注意细节

1、不管是重启系统还是关闭系统，首先要运行sync命令，把内存中的数据写到磁盘中

2、目前的shutdown/reboot/halt等命令均已经在关机前进行了sync

### 指定/修改密码

- 基本语法

>  passwd 用户名

- 应用案例

给milan指定密码

> 补充，显示当前用户所在的目录 pwd

### 删除用户

- 基本语法

> userdel 用户名

- 应用案例

1. 删除用户milan，但是要保留home目录 `userdel milan`
2. 删除用户以及用户主目录，比如Tom `userdel -r tom`

- 细节说明

是否保留home目录的讨论？

> 注：一般情况下，建议保留

### 查询用户信息指令

- 基本语法

> id 用户名

- 应用案例

案例：查询root 信息

- 细节说明

当用户不存在时，返回无此用户

### 切换用户

- 介绍

在操作Linux中，如果当前用户的信息权限不够，可以通过su - 指令，切换到高权限用户，比如root

- 基本语法

su - 切换用户名

- 应用实例

创建一个用户jack，指定密码，然后切换到jack

- 细节说明

1. 从权限高的用户切换到权限低的用户，不需要输入密码，反之需要。
2. 当需要返回到原来用户时，使用exit/logout指令

### 查看当前用户信息/登出用户

- 基本语法

whoami/who am I

### 用户组

- 介绍

类似于角色，系统可以对有共性/权限的多个用户进行统一的管理

- 新增组

指令：`groupadd 组名`

- 删除组

指令(基本语法)：groupadd 组名

案例演示

- 增加用户时直接加上组

指令(基本语法)：useradd -g 用户组 用户名

增加一个用户 zwj，直接将他指定到 wudang

```
groupadd wudang
useradd -g wudang zwj //增加一个用户，同时将这个用户放到wudang这个组
```



- 修改用户的组

指令：`usermod -g 用户组 用户名`

案例演示

创建一个组mojiao

把zwj放入到mojiao

### 用户和组相关文件

- /etc/passwd 文件

用(user)的配置文件，记录用户的各种信息

每行的含义：用户名：口令：用户标识号：组标识号：注释性描述：主目录：登录Shell



- /etc/shadow 文件

口令的配置文件

每行的含义：登录名:加密口令:最后一次修改时间:最小时间间隔:最大时间间隔:警告时间:不活动时间:失效时间:标志



- /etc/group

查看所有组及组内成员

组(group)的配置文件，记录Linux包含的组的信息

每行含义：组名:口令:组标识号:组内用户列表

## 运行级别

![image-20230421151014315](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421151014315.png)

### 指定运行级别

![image-20230421151431587](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421151431587.png![image-20230421151511295](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421151511295.png)

## 找回root密码

![image-20230421152240249](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421152240249.png)

![image-20230421152504176](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421152504176.png)

![image-20230421152713600](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421152713600.png)



## 帮助指令

![image-20230421153135603](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421153135603.png)

> 注：隐藏的文件是以 . 开头的，如果创建一个隐藏文件 则以 . 开头即可

## 文件目录指令

### cd指令

![image-20230421163929873](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230421163929873.png)

> 使用相对路径到/root目录， 比如当前绝对路径为/home/tom 则使用`cd../../root`即可到/root目录

### mkdir指令

mkdir 用于创建目录

基本语法：mkdir [选项] 要创建的目录

- 常用选项

> -p：创建多级目录

- 案例

案例1：创建一个目录 /home/dog

```
mkdir /home/dog
```



案例2：创建多级目录/home/animal/tiger

```
mkdir -p /home/animal/tiger
```



> 注：mkdir 默认只能创建一级目录，如果要创建多级目录使用指令 mkdir -p

### rmdir指令

删除空目录

- 基本语法

rmdir [选项] 要删除的空目录

- 应用实例

案例：删除一个目录 /home/dog

- 使用细节

rmdir 删除的是空目录，如果目录下有内容时是无法删除的。

提示：如果需要删除非空目录，需要使用 `rm -rf 要删除的目录`

比如：rm -rf /home/animal

### touch指令

touch指令创建空文件

- 基本语法

touch 文件名称

- 应用实例

创建一个空文件 hello.txt

` touch hello.txt`

### 拷贝指令

- cp指令

cp 指定拷贝文件到指定目录

- 基本语法

cp [选项] source dest

- 常用选项

-r：递归复制整个文件夹

- 应用实例

案例1：将/home/hello.txt 拷贝到 /home/bbb 目录下

`cp hello.txt /home/bbb`

案例2：递归复制整个文件夹，举例，比如将/home/bbb整个目录，拷贝到/opt

`cp -r /home/bbb /opt`

> 细节：强制覆盖不提示的方法：\cp , \cp -r /home/bbb/opt 强制覆盖且不提示

### rm指令

说明：rm指令移除文件或目录

- 基本语法

rm [选项] 要删除的文件或目录

- 常用选项

-r：递归删除整个文件夹 /home/bbb

-f：强制删除不提示

- 应用实例

案例1：将/home/hello.txt删除，rm /home/hello.txt

案例2：递归删除整个文件夹/home/bbb, rm -rf /home/bbb [删除整个文件夹，不提示]

> 细节：强制删除不提示的方法：带上 -f 参数即可



### mv指令

mv 移动文件与目录或重命名

- 基本语法

mv oldNameFile newNameFile (功能描述：重命名)

mv /temp/movefile /targetFolder (功能描述：移动文件)



- 应用实例

案例1：将/home/cat.txt 文件 重新命名为 pig.txt

案例2：将/home/pig.txt 文件移动到 /root 目录下

> 移动指令：mv /home/pig.txt /root         移动并重命名指令：mv /home/pig.txt /root/cat.txt

案例3：移动整个目录，比如将 /opt/bbb，移动到 /home下

mv /opt/bbb/ /home/



### cat指令

cat 查看文件内容（只能查看不能修改，建议查看重要文件时用cat)

- 基本语法

cat [选项] 要查看的文件

- 常用选项

-n：显示行号

- 应用实例

案例1：/etc/profile 文件内容，并显示行号

> 细节：cat只能浏览文件，不能修改文件，为了浏览方便，一般会带上 管道命令 | more (将前面处理的结果交给后面的命令继续执行)

`cat -n /etc/profile | more [进行交互]`

![image-20230429081149279](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230429081149279.png)

### less指令

![image-20230429093200042](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230429093200042.png)



### echo指令

echo输出内容到控制台

- 基本语法

echo [选项] [输出内容]

- 应用实例

案例：使用echo 指令输出环境变量，比如输出 $PATH $HOSTNAME   `echo $PATH`

案例：使用echo 指令输出 hello,world!



### head指令

head用于显示文件的开头部分内容，默认情况下head指令显示问价的前10行内容

- 基本语法

head 文件 (功能描述：查看文件头10行内容)

head -n 5 文件 (功能描述：查看文件头5行内容，5可以是任意行数)

- 应用实例

案例：查看/etc/profile 的前5行代码

head -n 5 /etc/profile

### tail指令

![image-20230429093801015](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230429093801015.png)

> 监控指令：tail -f /home/mydate.txt

### > 指令 和 >> 指令

![image-20230429094325529](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230429094325529.png)

> 注意：> 表示覆盖操作，>> 表示追加操作，不会覆盖目标文件，只会在文件末尾追加

### 	ln 指令

![image-20230429145814541](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230429145814541.png)



### history指令

查看已经执行过历史命令，也可以执行历史指令

- 基本语法

history(功能描述：查看已经执行过历史命令)

- 应用实例

案例1：显示所有的历史命令

`history`

案例2：查看最近使用过的10个指令

`history 10`

案例3：执行历史编号为5的指令

`!5`

## date指令-显示当前日期

- 基本语法

1.date					显示当前时间

2.date +%Y	       显示当前年份

3.date +%m	 	显示当前月份

4.date +%d	  	显示当前是那一天

3.date "+%Y-%m-%d %H:%M:%S"	  显示年月日时分秒



### 设置日期

> date -s 字符串时间

案例1：设置系统当前时间，比如设置成2020-11-03 20:02:10

`date -s "2020-11-03 20:02:10"`

### cal指令

查看日历

- 基本语法

cal [选项] (不加选项显示本月日历)

## 查找指令

### find指令

find指令将从指定目录向下递归地遍历其各个子目录，将满足条件的文件或目录显示在终端

- 基本语法

find [搜索范围] [选项]

> 选项说明：
>
> -name<查询方式> 		按照指定的文件名查找模式查找文件
>
> -user<用户名>			   查找属于指定用户名所有文件
>
> -size<文件大小>			按照指定的文件大小查找文件。

- 应用案例

案例1：按文件名：根据名称查找/home目录下的hello.txt文件

`find /home -name hello.txt`

案例2：按拥有者：查找/opt目录下，用户名称为nobody的文件

`find /opt -user nobody`

案例3：查找整个linux系统下大于200M的文件(+n 大于 -n 小于 n等于，单位有k,M,G)

`find / -size +200M`



### locate指令

locate指令可以快速定位文件路径。locate指令利用事先建立的系统中所有文件名称及路径的locate数据库实现快速定位给定的文件。Locate指令

无需比那里整个文件系统，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新locate时刻

- 基本语法

locate 搜索文件

> 特别说明：由于locate指令基于数据库进行查询，所以第一次运行前，必须使用updatedb指令创建locate数据库

- 应用实例

案例1：请使用locate指令快速定位hello.txt文件所在目录

```
	
updatedb

locate hello.txt
```

### which指令

可以查看某个指令在哪个目录下

案例：查找ls指令在哪个目录下

`which ls`



### grep指令和管道符 |

grep 过滤查找，管道符，“|”，表示将前一个命令的处理结果输出传递给后面的命令处理。

- 基本语法

grep [选项] 查找内容 源文件

- 常用选项

> -n	显示匹配行及行号
>
> -i	 忽略字母大小写

- 应用案例

在hello.txt文件中，查找"yes"所在行，并且显示行号

写法1：cat /home/hello.txt |grep -n "yes"

写法2：grep -n "yes" /home/hello.txt

## 压缩和解压

### gzip/gunzip 指令

gzip用于压缩文件，gunzip用于解压的

- 基本语法

gzip文件		(功能描述：压缩文件，只能将文件压缩为*.gz文件)

gunzip 文件.gz	(功能描述：解压缩文件命令)

- 应用实例

案例1：gzip压缩，将/home下的hello.txt文件进行压缩

gzip /home/hello.txt

案例2：gunzip压缩，将/home下的hello.txt.gz文件进行解压缩

gunzip /home/hello.txt.gz



### zip/unzip 指令

![image-20230430111903976](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230430111903976.png)

案例1：将/home下的 所有文件/文件夹进行压缩成 myhome.zip

>  zip -r myhome.zip /home/ (将home目录及其包含的文件和子文件夹都压缩)

案例2：将 myhome.zip 解压到 /opt/tmp 目录下

> mkdir /opt/tmp
>
> unzip -d /opt/tmp   /home/myhome.zip

### tar 指令

![image-20230430113526197](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230430113526197.png)

案例1：压缩多个文件，将/home/pig.txt 和 /home/cat.txt 压缩成pc.tar.gz

> tar -zcvf pc.tar.gz /home/pig.txt /home/cat.txt

案例2：将/home 的文件夹 压缩成 myhome.tar.gz

>  tar -zcvf myhome.tar.gz /home/

案例3：将pc.tar.gz 解压到当前目录，切换到 /opt/

> tar -zxvf pc.tar.gz

案例4：将myhome.tar.gz 解压到 /opt/tmp2目录下

> mkdir /opt/tmp2
>
> tar -zxvf  /home/myhome.tar.gz -C /opt/tmp2

## Linux组管理和权限管理

### 基本介绍

在linux中的每个用户必须属于一个组，不能独立于组外。

在linux中**每个文件有所有者**、所在组、其他组的概念。

1、所有者

2、所在组

3、其他组

4、改变用户所在组

 示意图：

![image-20230430155730249](C:\Users\Administrator.DESKTOP-KQRCAUT\AppData\Roaming\Typora\typora-user-images\image-20230430155730249.png)

a.txt是tom创建的，那么tom是a.txt的所有者，tom是属于组1的，所以组1里面的成员对a.txt也有一定的权限

组2对于a.txt而言 就是其他组，其他组对a.txt也有一定的权限

### 查看文件所有者

- 查看文件所有者

指令：ls -ahl

- 修改文件所有者

指令：chown 用户名 文件名

- 应用案例

要求：使用root创建一个文件apple.txt，然后将其所有者修改成tom

> touch apple.txt
>
> chown tom apple.txt



### 组的创建

- 基本指令

> groupadd 组名

- 应用实例

创建一个组，monster

>  groupadd monster

创建一个用户fox，并放入到 monster组中

> useradd -g monster fox

### 文件/目录 所在组

当某个用户创建了一个文件后，这个文件的所在组就是该用户所在的组。

- 查看文件/目录所在组

> 基本指令：ls -ahl

- 应用实例

使用fox来创建一个文件，看看该文件属于哪个组

> 文件属于fox所在的monster组

- 修改文件所在组

> 基本指令：chgrp 组名 文件名

- 应用实例

使用root用户创建文件 orange.txt，看看当前这个文件属于哪个组，然后将这个文件所在组，修改到fruit组。

> groupadd fruit
>
> touch orange.txt
>
> 看看这个文件属于哪个组 -> root组
>
> chgrp fruit orange.txt

### 改变用户所在组

在添加用户时，可以指定将该用户添加到哪个组中，同样的用root的管理权限可以改变某个用户所在的组

- 改变用户所在组

> 1、usermod -g 组名 用户名
>
> 2、usermod -d 目录名 用户名 改变该用户登录的初始目录。

- 应用实例

将zwj这个用户从原来所在组，修改到wudang组

## 权限的基本介绍

ls -l 中显示的内容如下：

```
-rwxrw-r-- 1 root root 1213 Feb 2 09:39 abc
```

0-9位说明

> 1、第0位(-)确定文件类型(d, - , l , c , b)
>
> \- 是普通文件
>
> l 是链接，相当于windows的快捷方式
>
> d 是目录，相当于windows的文件夹
>
> c 是字符设备文件，鼠标，键盘
>
> b 是块设备，比如硬盘
>
> 2、第1-3位(rwx)确定所有者(该文件的所有者)拥有该文件的权限。 ---User
>
> 3、第4-6位(rw-)确定所属组(同用户组的)拥有该文件的权限，---Group
>
> 4、第7-9位(r--)确定其他用户拥有该文件的权限 ---Other

### rwx权限详解，难点

- rwx作用到文件

1、[r] 代表可读

2、[w] 代表可写：可以修改，但是不代表可以删除该文件，**删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件**

3、[x] 代表可执行(execute)

- rwx作用到目录

1、[r] 代表可读：可以读取，ls查看目录内容

2、[w] 代表可写：可以修改，对目录内创建+删除+重命名目录

3、[x] 代表可执行：可以进入该目录

![image-20230501134234601](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230501134234601.png)



### 修改权限-chmod

- 基本说明：通过chmod指令，可以修改文件或者目录的权限



- 第一种方式：+、-、= 变更权限

u：所有者 g：所有组 o：其他人 a：所有人(u、g、o的总和)

```
1.chmod u=rwx,g=rx,o=x 文件/目录名
2.chmod o+w 文件/目录名
3.chmod a-x 文件/目录名
```

案例演示：

1. 给abc文件的所有者读写执行的权限，给所在组读执行权限，给其他组读执行权限。

> chmod u=rwx,g=rx,o=rx abc

1. 给abc文件的所有者除去执行的权限，增加组写的权限

> chmod u-x,g+w abc

1. 给abc文件的所有用户添加读的权限

> chmod a+r abc

- 第二种方式：通过数字变更权限

![image-20230501140249575](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230501140249575.png)

### 修改文件所有者

- 基本介绍

chown newowner 文件/目录 改变所有者

chown newowner:newgroup 文件/目录 改变所有者和所在组

-R 如果是目录 则使其下所有子文件或目录递归生效

- 案例演示

请将 /home/abc.txt文件的所有者修改成 tom

> chown tom /home/abc.txt

请将 /home/kkk 目录下所有的文件和目录的所有者都修改成tom

> chown -R tom /home/kkk

### 修改文件/目录所在组 -chgrp

- 基本介绍

chgrp newgroup 文件/目录 【改变所在组】

- 案例演示

请将 /home/abc.txt 文件的所在组修改成 shaolin(少林)

> chgrp shaolin /home/abc.txt 

请将/home/kkk目录下所有的文件和目录的所在组修改成shaolin(少林)

> chgrp -R shaolin /home/kkk
