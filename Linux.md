# Linux 概述

最广泛的应用领域：服务器

# Linux 与 Unix

# 网络的连接方式

1.桥接模式：虚拟系统可以和外部系统通讯，但是容易造成IP冲突。

2.NAT模式：网络地址转化模式，虚拟系统可以和外部系统通讯，不造成IP冲突。

3.主机模式：独立的系统（单机，不能联网）

![](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220712121643508.png)

李四ping不通88，88ping的了李四

# Linux 目录结构

## 基本介绍

1. Linux的文件系统是采用级层式的树状目录结构，在此结构中的最上层是“根目录”，然后在此目录下再创建其他的目录。
2. 深刻理解Linux树状文件目录是非常重要的。

- **在Linux世界里，一切皆文件**

- **Linux会把硬件映射成软件管理**

  <img src="C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713182111451.png" alt="image-20220713182111451" style="zoom: 50%;" />

## 目录结构详解

|             目录结构             |                           存储内容                           |
| :------------------------------: | :----------------------------------------------------------: |
| **/bin /usr/bin /usr/local/bin** |      bin 是 Binary 的缩写，该目录存放着最经常使用的命令      |
| /sbin /usr/sbin /usr/local/sbin  | s 是 Super User 的缩写，该目录存放的是系统管理员使用的系统管理程序 |
|            **/home**             | 存放普通用户的主目录，在 Linux 中每个用户都有一个自己的目录，一般该目录名是以用户的账号命名 |
|            **/root**             |       该目录为系统管理员，也称作超级权限者的用户主目录       |
|               /lib               | 系统开机所需要最基本的动态连接共享库，其作用类似于 Windows 里的 DLL 文件。几乎所有的应用程序都需要用到这些共享库 |
|           /lost+found            | 该目录一般情况下是空的，当系统非法关机后，这里就存放一些文件 |
|             **/etc**             |        所有的系统管理所需要的配置文件和子目录 my.conf        |
|             **/usr**             | 该目录非常重要，用户的很多应用程序和文件都放在这个目录下，类似 Windows 下的 Program files 目录 |
|            **/boot**             | 存放的是启动 Linux 时使用的一些核心文件，包括一些连接文件以及镜像文件 |
|              /proc               | 该目录是一个虚拟的目录，它是系统内存的映射，访问这个目录来获取系统信息 |
|               /srv               | srv 是 service 的缩写，该目录存放一些服务启动之后需要提取的数据 |
|               /sys               | 这是 Linux 2.6 内核的一个很大的变化。该目录下安装了 2.6 内核中新出现的一个文件系统 sysfs |
|               /tmp               |                 该目录是用来存放一些临时文件                 |
|               /dev               |  类似于 Windows 的设备管理器，把所有的硬件用文件的形式存储   |
|             **/mnt**             | 系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将外部的存储挂载在 /mnt 上,然后进入该目录就可以查看里的内容了。D:\myshare |
|            **/media**            | Linux 系统会自动识别一些设备，例如U盘、光驱等等，当识别后，Linux 会把识别的设备挂载到该目录下 |
|               /opt               | 主机额外安装软件所存放的目录。如安装 ORACLE 数据库就可放到该目录下。默认为空 |
|          /**usr/local**          | 该目录是另一个给主机额外安装软件所安装的目录。一般是通过编译源码方式安装的程序 |
|             **/var**             | 该目录中存放着在不断扩充着的东西，习惯将经常被修改的目录放在目录下。包括各种日志文件 |
|             /selinux             | SELinux 是一种安全子系统，它能控制程序只能访问特定文件，有三种工作模式，可以自行设置。 |

# Vi 与 Vim

​		Linux 系统会内置 Vi 文本编辑器。Vim 具有程序编辑的能力，可以看做是 Vi 的增强版本，可以主动的以字体颜色辨别语法的正确性方便程序设计。代码补完、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用。

## 模式

1. 正常模式


​		以 Vim 打开一个档案就直接进入一般模式了（这是默认的模式）。在这个模式中，你可以使用『上下左右」按键来移动光标，你可以使用『删除字符」或『删除整行来处理档案内容，也可以使用『复制、粘贴」来处理你的文件数据。

2. 插入模式

​		按下i,I,o,O,a,A,r,R等任何一个字母之后才会进入编辑模式，一般来说按 i 即可。

3. 命令行模式

​		输入esc再输入：在这个模式当中，可以提供你相关指令，完成读取、存盘、替换、离开Vim、显示行号等的动作则是在此模式中达成的。

​		:wq    write quit 保存退出

​		:q! 	强制退出不保存

​		:q 		退出

## 快捷键

1.拷贝当前行

yy,拷贝当前行向下的5行5yy,并粘贴。
2.删除当前行dd,删除当前行向下的5行5dd
3.在文件中查找某个单词[命令行下/关键字，回车查找，输入就是查找下一个]
4.设置文件的行号，取消文件的行号。[命令行下：set nu和：:set nonu]
5.编辑/etc/profile文件，使用快捷键到该文档的最末行[G]和最首行[gg]
6.在一个文件中输入"hello”，然后又撤销这个动作u
7.编辑/etc/profile文件，并将光标移动到20行shift+g
8.更多的看整理的文档

![image-20220712131253742](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220712131253742.png)

N上一个 n下一个

# 开机重启注销

**shutdown 默认是 shudown -h 1  **

- 立该进行关机，h → halt 停止

  ```Linux
  shutdown -h now 
  ```

- 1分钟后关机

  ``` Linux
  shudown -h 1  
  ```

- 立刻重启计算机，r → reboot 重启

  ``` Linux
  shutdown -r now
  ```

- `halt`  关机，作用和上面一样

- `reboot`   现在重新启动计算机

- `sync`  把内存的数据同步到磁盘，sync → synchronization 同步

# 用户管理

​		Linux 系统是一个多用户多任务的操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。

- 基本介绍

​		1.登录时尽量少用root帐号登录，因为它是系统管理员，最大的权限，避免操作失误。可以利用普通用户登录，登录后再用 `su username` 命令来切换成系统管理员身份。

​		2.在提示符下输入`logout`即可注销用户

- 使用细节
  `logout`注销指令在图形运行级别无效，在运行级别 3 下有效。

## 添加用户

- 基本语法

  ```shell
  useradd usrname
  ```

- 应用案例：添加一个用户 uriku，默认该用户的家目录在 /home/uriku
  
- 细节说明
  1.当创建用户成功后，会自动的创建和用户同名的家目录
  2.也可以指定目录

  ``` linux
  useradd -d /ss/ss
  ```


  新的用户名，给新创建的用户指定家目录所示:所示

## 指定/修改密码

- 基本语法

  ``` Linux
  passwd uriku
  ```

- 应用案例
  案例：给用户 uriku 指定密码

- 补充

  显示当前用户所在的目录 `pwd`

## 删除用户

- 基本语法

  ``` Linux
  userdel username
  ```

- 应用案例

  案例1：删除用户 uriku，但是要保留家目录

  ```Linux
  userdel uriku
  ```

  案例2：删除用户以及用户家目录，比如 kirito

  ``` Linux
  userdel -r kirito
  ```

- 细节说明

  是否保留家目录？一般情况下，我们建议保留

## 查询用户信息

- 基本语法

  ``` Linux
  id username
  ```

- 应用实例

  查询 root 信息

- 补充说明

  当用户不存在时，返回无此用户

## 切换用户

- 介绍

  在操作 Linux 中，如果当前用户的权限不够，可以通过`su - username`，切换到高权限用户，比如 root

- 基本语法

  ``` Linux
  su - username
  ```

- 应用实例

  创建一个用户 alice,指定密码，然后切换到 alice

- 细节说明

  1.从权限高的用户切换到权限低的用户，不需要输入密码，权限低的用户切换到权限高的和用户权限一样的用户，需要输入密码
  2.当需要返回到原来用户时，使用 `exit`,`logout`指令

## 查看当前用户/登录用户

- 基本语法

  ``` Linux
  who am i   whoami
  ```

- 补充说明

  查看的是初始身份，即使使用了 `su - username` 命令还是显示切换前的信息

## 用户组

- 介绍

  类似于角色，系统可以对有共性的多个用户进行统一的管理。用户权限一致的可以视为一个用户组。

- 新增组

  ``` Linux
  groupadd groupname
  ```

- 删除组

  ``` Linux
  groupdel groupname
  ```

- 增加用户时直接加上组

  ```Linux
  useradd -g groupname username
  ```

  **新增用户没有添加组时，同时会默认创建一个同名的组**

  - 应用案例

    增加一个用户 asuna，直接将他指定到 sao

    ```Linux
    useradd -g sao asuna
    ```

- 修改用户的组，mod → modify 修改

  ``` Linux
  usermod -g groupname username
  ```

  - 应用实例

    创建一个组 rw，把 alice 放入到 rw

    ```Linux
    usermod -g rw alice
    ```

## 用户和组相关文件

![image-20220712143547505](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220712143547505.png)

# 运行级别

- 基本介绍
  运行级别说明：
  0：关机
  1：单用户【找回丢失密码】
  2：多用户状态没有网络服务（用的少）
  3：多用户状态有网络服务（用的最多，没有图形界面）
  4：系统未使用保留给用户（用的少）
  5：图形界面
  6：系统重启

  常用运行级别是 3 和 5，也可以指定默认运行级别，后面演示

- 应用实例

  ``` Linux
  init [0123456]
  ```

- 应用案例

  通过init来切换不同的运行级别，比如动 5-3，然后关机。

## 指定运行级别

multi-user.target：运行级别为3，多用户有网络服务 

graphical.target：运行级别为5，有图形界面 

- 查看当前运行级别

  ```Linux
  systemctl get-default 
  ```

- 设置默认级别为 3

  ``` Linux
  systemctl set-default multi-user.target
  ```

## 找回 Root 密码

百度

# 帮助指令

## man 获得帮助信息

- 基本语法

  man【命令或配置文件】(功能描述：获得帮助信息)

- 应用实例

  查看 ls 命令的帮助信息

  ```Linux
  man ls
  ```
  
- 汉化指令

  1. 安装中文版 man 指令

     ```shell
     yum update
     
     yum install man-pages-zh-CN
     ```

  2. 默认语言修改成中文

     ```shell
     vim /etc/locale.conf 
     ```

     >  LANG="zh_CN.UTF-8"
     >
     >  LANGUAGE="zh_CN.GB18030:zh_CN.GB2312:zh_CN"
     >
     >  SUPPORTED="zh_CN.UTF-8:zh_CN:zh:en_US.UTF-8:en_US:en"
     >
     >  SYSFONT="lat0-sun16"


  在Linux下，隐藏文件是以开头，选项可以组合使用比如`ls - al`，比如`ls - al /root`

## help指令

- 基本语法

  help 命令(功能描述：获得shellp内置命令的帮助信息)

- 应用实例

  查看cd命令的帮助信息

# 文件目录类

![image-20220712183334915](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220712183334915.png)

绝对路径：

相对路径：



## pwd 指令

- 基本介绍

  显示当前工作目录的绝对路径

- 基本语法

  ``` shell
  pwd
  ```

- 应用实例：显示当前工作目录的绝对路径


## ls 指令

- 基本语法

  ```Linux
  ls [选项] [目录]
  ```

- 常用选项

  `-a` → 显示当前目录所有的文件和目录，包括隐藏的内容

  `-l `→ l 以列表的方式显示信息

  -`h` → human

  `-ld` 显示目录属性

- 应用实例

  查看当前目录的所有内容信息

## cd 指令

- 基本介绍

  切换到指定目录

- 基本语法

  ```` Linux
  cd [选项]
  ````

- 常用选项

  
  
  
  
- 应用案例

  - 案例1：使用绝对路径切换到 root 目录
  - 案例2：使用相对路径到 root 目录
  - 案例3：表示回到当前目录的上一级目录
  - 案例4：回到家目录

![image-20220712183737981](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220712183737981.png)









![image-20220713101547296](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713101547296.png)

## mkdir 指令

make 目录

![image-20220713101909387](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713101909387.png)

## rmdir 指令

- 基本介绍

  `rmdir` 指令删除空目录。rmdir 是 remove directory 的缩写

- 基本语法

  ```shell
  rmdir [选项] [目录]
  ```

- 常用选项

- 应用案例：删除一个目录 /home/dog

  ```shell
  rmdir /home/dog
  ```

- 注意事项

  1. `rmdir ` 指令删除的是空目录，如果目录下有内容时无产法删除的
  2. 如果需要删除非空目录，需要使用 `rm-rf [目录]`

## touch 指令

- 基本介绍

  touch 指令创建空文件

- 基本语法

  ```shell
  touch 文件名
  ```

- 应用案例：在 /home 目录下，创建一个空文件 hello.txt

  ``` shell
  touch /home/hello.txt
  ```

## cp 指令

- 基本介绍

  `cp` 指令拷贝文件/目录到指定文件/目录。 cp 是 copy 的缩写

- 基本语法

  ```shell
  cp [选项] [目标目录]
  ```

- 常用选项
  | 选项 |   全称    |             描述             |
  | :--: | :-------: | :--------------------------: |
  |  -r  | recursive | 指定目录向其下级目录递归复制 |
  
  递归复制整个文件夹，当前目录也会复制
  
  ```shell
  cp -r [目标目录]
  ```
  
 - 使用细节：强制覆盖不提示的方法

   ```shell
   \cp [选项] [目标目录]
   ```
   
 - 应用案例

   - 案例1：将 /home/hello.txt 拷贝到 /home/bbb 目录下

     ```shell
     cp /home/hello.txt /home/bbb
     ```

     案例2：递归复制整个文件夹。举例，将 /home/bbb 整个目录，拷贝到 /opt

     ```shell
     cp -r /home/bbb /opt
     ```

## rm 指令

- 基本介绍

  `rm` 指令删除指定文件/目录。rm 是 remove 的缩写

- 基本语法

  ```Linux
  rm [选项] [目录]
  ```

- 常用选项

  | 选项 |   全称    |                  描述                  |
  | :--: | :-------: | :------------------------------------: |
  |  -r  | recursive | 指定目录向其下级目录递归删除整个文件夹 |
  |  -f  |   force   |             强制删除不提示             |


 - 应用实例

   - 案例1：将 /home/hello.txt 删除

     ```shell
     rm /home/hello.txt
     ```

   - 案例2：递归删除整个文件夹 /home/bbb（删除整个文件夹，不提示）

     ```shell
     rm -rf /home/bbb
     ```

## mv 指令

- 基本介绍

  `mv` 指令移动文件与目录或重命名。mv 是 move 的缩写。

- 基本语法

  - 重命名

      ```shell
      mv oldfilename newfilename

  - 移动文件/目录

      ```shell
      mv temp/movefile /targetFolder
      ```

 - 应用案例

   - 案例1：将 /home/cat.txt 文件重新命名为 pig.tbxt

     ```shell
     mv /home/cat.txt pig.txt
     ```

   - 案例2：将 /home/pig.txt 文件移动到 /root目录下

     ```shell
     mv /home/pig.txt /root
     ```
     
   - 案例3：将 /opt/bbb 移动到 /home下

     ```shell
     mv /opt/bbb /home
     ```

## cat 指令

- 基本介绍

  `cat` 指令查看文件内容

- 基本语法

  ```shell
  cat [选项] [文件]
  ```

- 常用选项

  | 选项 | 全称 |   描述   |
  | :--: | :--: | :------: |
  |  -n  |      | 显示行号 |

- 使用细节

  cat 只能浏览文件，而不能修改文件，为了浏览方便，一般会带上管道命令 | more

  **加上了 more 的管道命令 cat 指令，快捷键和 more 指令一致**

  ```shell
  cat -n/ etc/profile | more
  ```

- 应用案例：查看 /etc/profile 文件内容，并显示行号

  ```shell
  cat -n/ etc/profile | more
  ```

## more 指令

- 基本介绍

  `more` 指令是一个基于 VI 编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容

- 基本语法

  ```shell
  more [文件]
  ```

- 快捷键

  |  快捷键  |               描述                |
  | :------: | :-------------------------------: |
  |  空格键  |            向下翻一页             |
  |  Enter   |            向下翻一行             |
  |    q     | 立刻离开 more，不再显示该文件内容 |
  | Ctrl + F |           向下滚动一屏            |
  | Ctrl + B |            返回上一屏             |
  |    =     |         输出当前行的行号          |
  |    :f    |     输出文件名和当前行的行号      |

- 应用案例：采用 more 查看文件 /etc/profile

  ```shell
  more /etc/profile
  ```

## less 指令

​	less 指令用来分屏查看文件内容，它的功能与 more 指令类似，但是比 more 指令更加强大，支持各种显示终端。less 指令在显示文件内容时，并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高的效率。

- 基本语法

- 操作

  |   操作   | 功能说明 |
  | :------: | :------: |
  |          |          |
  |  PageUp  |          |
  | PageDown |          |
  | /字符串  |          |
  | ?字符串  |          |
  |    q     |          |

  

- 应用实例

![](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713113949364.png)

## echo 指令

![image-20220713114952531](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713114952531.png)

## head 指令



## tail 指令

![image-20220713114936484](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713114936484.png)



## > 与 >> 指令

![image-20220713120023623](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713120023623.png)

覆盖

》追加

## ln 指令

link

![image-20220713121529957](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713121529957.png)

## histroy 指令

![image-20220713121517621](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713121517621.png)



# 时间日期类

## date 指令

- 基本语法

![image-20220713121949114](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713121949114.png)



![image-20220713122338621](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713122338621.png)

## cal 指令



# 搜索查找类

## find 指令

![image-20220713123233464](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713123233464.png)

## locate 指令

![image-20220713123703614](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713123703614.png)

## grep 指令和管道符号 |

![image-20220713124550352](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713124550352.png)

# 压缩和解压类

## gzip/gunzip 指令

## ![image-20220713124812394](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713124812394.png)zip/unzip 指令

![image-20220713125908885](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713125908885.png)

## tar 指令

![image-20220713141313128](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713141313128.png)

# Linux 组

## 组的基本介绍

​		在 Linux 中的每个用户必须属于一个组，不能独立于组外。在 Linux 中每个文件有所有者、所在组、其它组的概念。

- 所有者

- 所在组

   - 其他组

     除文件的所有者和所在组的用户外，系统的其它用户都是文件的其它组

- 改变用户所在的组

  

## 文件/目录的所有者

​		一般为文件的创建者，谁创建了该文件，就自然的成为该文件的所有者。

![image-20220713142401558](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713142401558.png)

- 查看文件的所有者

  ``` Linux
  ls-ahl
  ```


- 修改文件所有者

  ```Linux
  chown username filename
  ```

- 应用案例
  使用 root 创健一个文件 apple.txt，然后将其所有者修改成 tom

  ``` Linux
  chown tom apple.txt
  ```

## 文件/目录的所在组

- 创建组基本指令

  ```Linux
  gourpadd groupname
  ```

- 创建用户并加入指定组基本指令

  ```Linux
  useradd -g groupname username
  ```

- 应用实例

  创键一个组 monster，创键一个用户 fox，并放入到 monster 组中

  ```Linux
  groupadd monster
  useradd -g monster fox
  ```

​		当某个用户创建了一个文件后，这个文件的所在组就是该用户所在的组。

- 修改文件所在的组

  ```Linux
  chgrp groupname filename
  ```
  
- 应用实例
  使用 root 用户创建文件 orange.txt 看看当前这个文件属于哪个组，然后将这个文件所在组，修改到fruit 组
  
  ```Linux
  touch orange.txt 
  ls -lah
  chgrp fruit orange.txt
  ```

## 改变用户所在的组

​		在添加用户时，可以指定将该用户添加到哪个组中，同样的用 root 的管理权限可以改变某个用户所在的组。

- 改变用户所在组

  ```Linux
  usermod -g newgroupname username
  ```

  ```Linux
  usermod -d dirname username 改变该用户登陆的初始目录
  ```

  **用户需要有进入到新目录的权限**

- 应用实例

  将 alice 这个用户从原来所在组，修改到 rw 组

  ```Linux
  usermod -g rw alice
  ```

# 权限

## 权限位

第一列：0-9 10位

0-9位说明
1.

第0位确定文件类型(d,-,I,c,b)

​	I → Link，代表链接，相当于 windows 的快捷方式

​	d → Diretory，代表目录，相当于 windows 的文件夹

​	c → character，代表字符设备文件，鼠标，键盘

​	b → block，代表块设备，比如硬盘

​    -，代表普通文件



2.

第1-3位确定所有者（该文件的所有者）拥有该文件的权限。--User

3.

第4-6位确定所属组（同用户组的）拥有该文件的权限，--Group

4.第7-9位确定其他用户拥有该文件的权限-Other

![image-20220713144952105](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713144952105.png)

## rwx 权限详解

- rwx 作用到文件
  - r → read，代表可读，查看
  - w → write，代表可写（write:可以修改，但是不代表可以删除该文件，删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件）
  - x → execute，代表可执行

- rwx作业到目录
  - r → read，代表可读，`ls`查看目录内容
  - w → write，代表可写，对目录内创建删除重命名目录
  - x → execute，代表访问，`cd`进入该目录（一定要先x才能说rw）

## 权限案例





![image-20220713150957110](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713150957110.png)

## 修改权限

- 基本介绍

  

![image-20220713152107280](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713152107280.png)

![image-20220713152509166](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713152509166.png)

## 修改文件/目录所有者

- 基本介绍
- 
- 应用实例

![image-20220713181430498](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713181430498.png)

## 修改文件/目录所在组

![image-20220713181817871](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220713181817871.png)

## 权限管理应用实例

- 警察和土匪游戏

  | 用户  |   组   |
  | :---: | :----: |
  | jack  | police |
  | jerry | police |
  | uriku | bandit |
  | eugeo | bandit |

  - 创建组

    ```Linux
    ```

  - 创建用户

    ```Linux
    
    ```

  - jack 创建一个文件，自己可以读写，本组人可以读，其他组没有任何权限

    ```Linux
    ```

  - jack 修改文件，让其他组人可以读，本组人可以读写

    ```Linux
    ```

  - uriku 投靠警察，是否可以读写

    

    不能，如果要对目录的文件进行操作，需要有对该目录的相应权限

![image-20220714113732601](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714113732601.png)



- - 目录所在组权限

  r 可以把目录下的文件列举出来 `ls`

  w 可以把目录下的文件增加删除 

  x



- ![image-20220714124137581](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714124137581.png)

# 定时任务调度

## crontab 指令

- 基本介绍

  任务调度：

  任务调度分类：

  个别人用户工作：

- 基本语法

  ```Linux
  crontab [选项]
  ```

- 常用选项

  | 选项 | 全称 | 描述 |
  | :--: | :--: | :--: |
  |  -e  |      |      |
  | -l-  |      |      |
  |  -r  |      |      |

  

![image-20220714124631070](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714124631070.png)

- 快速入门

  

  



![image-20220714125000770](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714125000770.png)

文件删了，设置了定时任务还是会执行，执行后会再次生成

![image-20220714125543922](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714125543922.png)

- 特殊符号

  | 特殊符号 | 含义 | 例子 |
  | :------: | :--: | :--: |
  |    *     |      |      |
  |    ,     |      |      |
  |    -     |      |      |
  |   */n    |      |      |

  ![image-20220714125830993](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714125830993.png)

- 特殊时间执行任务案例

![image-20220714125843180](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714125843180.png)

- 应用案例

  案例1:每隔1分钟，就将当前的日期信息，追加到 /tmp/mydate文件中

  ```Linux
  crontab -e
  */1 * * * * date >> /tmp/mydate
  ```

  案例2：每隔1分钟，将当前日期和日历都追加到 /home/mycal文件中

  ```Linux
  vim /home/my.sh
  date >> /home/mycal
  cal >> /home/mycal
  chmod u+X/home/my.Sh
  crontab-e
  */1****/home/my.sh
  ```

  

![image-20220714131512253](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714131512253.png)

## at 指令

- 基本介绍

  1. at 命令是一次性定时计划任务，at 的守护进程 atd 会以后台模式运行，检查作业队列来运行。

  2. 默认情况下，atd 守护进程每 60 秒检查作业队列，有作业时，会检查作业运行时间，如果时间与当前时间匹配，则运行此作业。

  3. at 命令是一次性定时计划任务，执行完一个任务后不再执行此任务了

  4. 在使用 at 命令的时候，一定要保证 atd 进程的启动，可以使用相关指令来查看

     `ps -ef | grep atd`检测 atd 是否在运行

- 基本语法

  ```Linux
  at [选项] [时间]
  ```

- 常用选项

  |      |      |      |
  | ---- | ---- | ---- |
  |      |      |      |
  |      |      |      |
  |      |      |      |
  |      |      |      |

  

- 

- 

- 

  Ctrl + D 结束 at 命令的输入

- 时间定义
- ![image-20220714133117509](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714133117509.png)

- 应用案例

  - 案例1：

    ```Linux
    at 5pm + 2days
    /bin/ls /home    ls /home
    ```

  - 案例2：

    ```Linux
    ```

    ![image-20220714134216532](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714134216532.png)

# 磁盘

## 磁盘分区

- 基本介绍

  1. Linux 文件结构，Linux 中每个分区都是用来组成整个文件系统的一部分。

  2. Linux 采用了一种叫"载入"的处理方法，它的整个文件系统中包含了一整套的文件和目录，且将一个分区和一个目录联系起来。这时要载入的一个分区将使它的存储空间在一个目录下获得。

  3. 示意图

     ![image-20220714135055082](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714135055082.png)

- 硬盘说明
  1. Linux 硬盘分 IDE 硬盘和 SCSI 硬盘，目前基本上是SCSI硬盘
  2. 对于IDE硬盘，驱动器标识符为“hdx~”，其中 hd 表明分区所在设备的类型，这里是指 IDE 硬盘了。“x”为盘号(a 为基本盘，b 为基本从属盘，c 为辅助主盘，d 为辅助从属盘，v 为虚拟盘)，”~”代表分区，前四个分区用数字 1 到 4 表示，它们是主分区或扩展分区，从5开始就是逻辑分区。例，hda3 表示为第一个 IDE 硬盘上的第三个主分区或扩展分区，hdb2 表示为第二个 IDE 硬盘上的第二个主分区或扩展分区。
  3. 对于 SCSI 则标识为“sdx~”，SCSI 硬盘是用”sd”来表示分区所在设备的类型的，其余则和 IDE 硬盘的表示方法一样。

- 查看所有设备挂载的硬盘

  ![image-20220714135910811](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714135910811.png)

- 经典案例

  下面我们以增加一块硬盘为例来熟悉下磁盘的相关指令和深入理解磁盘分区、挂载、卸载的概念

  - 如何增加一块硬盘

    1. 虚拟机添加硬盘

       ![image-20220714141612132](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714141612132.png)

    2. 分区

       ![image-20220714142210872](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714142210872.png)

    3. 格式化

       ![image-20220714142230274](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714142230274.png)

    4. 挂载

    5. 设置可以自动挂载

       ![image-20220714143129252](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714143129252.png)



![image-20220714143341874](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714143341874.png)

![image-20220714143534400](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714143534400.png)

## 磁盘情况查询

- 基本语法

  ```Linux
  df -h
  ```

- 应用案例

  ![image-20220714143817602](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714143817602.png)

## 查询指定目录的磁盘占用情况

- 基本语法

  ```Linux
  du [选项] [dir]
  ```

  不带目录就是默认当前目录

- 常用选项

  | 选项 | 全称 | 描述 |
  | :--: | :--: | :--: |
  |  -s  |      |      |
  |  -h  |      |      |
  |  -a  |      |      |
  |  -c  |      |      |

  ![image-20220714144320006](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714144320006.png)

- 应用案例

  查询 /opt 目录的磁盘占用情况，深度为 1

  

## 常用磁盘情况指令

![image-20220714145130910](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714145130910.png)

# 网络配置

## NAT 网络原理图

![image-20220714152918504](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714152918504.png)

![image-20220714153220189](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714153220189.png)

![image-20220714153505437](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714153505437.png)

![image-20220714153851584](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714153851584.png)

## IP 指定

![image-20220714154108809](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714154108809.png)



![image-20220714154641827](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714154641827.png)

![image-20220714155026416](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714155026416.png)

![image-20220714160110189](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714160110189.png)

![image-20220714160815251](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714160815251.png)

# 进程管理

- 基本介绍
  1. 在 Linux 中，每个执行的程序都称为一个进程。每一个进程都分配一个 ID号 (pid,进程号)。
  2. 每个进程都可能以两种方式存在的。前台与后台，所谓前台进程就是用户目前的屏幕上可以进行操作的。后台进程则是实际在操作，但由于屏幕上无法看到的进程，通常使用后台方式执行。
  3. 一般系统的服务都是以后台进程的方式存在，而且都会常驻在系统中。直到关机才才结束。

## ps  指令

- 基本介绍

  `ps`命令是用来查看目前系统中，有哪些正在执行，以及它们执行的状况。可以不加任何参数，

- 基本用法

  ```Linux
  ps [选项]
  ```

- 常用选项

  | 选项 | 全称 | 描述 |
  | :--: | :--: | :--: |
  |  -a  |      |      |
  |  -u  |      |      |
  |  -x  |      |      |
  |      |      |      |

  aux 和 ef 效果一样只是风格不同

  ```Linux
  ```

  USER：进程执行用户

  PID：进程号

  %CPUL：占用 CPU 的百分比

  %MEM：占用物理内存的百分比

  VSZ：占用虚拟内存的百分比

  RSS：

  TTY：终端信息

  STAT：当前运行的状态

  START：执行的开始时间

  TIME：占用 CPU 的时间

  COMMAND：执行进程的指令

  ![image-20220714161820072](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714161820072.png)

- 使用细节

  ![image-20220714162345507](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220714162345507.png)

  

- 应用案例

##  kill  allkill 指令

- 基本介绍

  若是某个进程执行一半需要停止时，或是已消了很大的系统资源时，此时可以考虑停止该进程。使用kill命令来完成此顶任务。

- 基本语法

  - 通过进程号终止进程

    ```Linux
    kill [选项] pid
    ```

  - 通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变得很慢时很有用

    ```Linux
    killall 进程名称
    ```

- 常用选项

  ![image-20220715122742163](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715122742163.png)

## pstree 指令

- 基本介绍

  以树状的方式显示进程信息，可以更加直观的来看进程信息

- 基本语法

  ```Linux
  pstree [选项]
  ```

- 常用选项

  | 选项 | 全称 |        描述        |
  | :--: | :--: | :----------------: |
  |  -p  | pid  |   显示进程的 pid   |
  |  -u  | user | 显示进程执行的用户 |

- 应用案例

  - 案例1：以树状的形式显示进程的 pid

    ```Linux
    pstree -p
    ```

  - 案例2：以树状的形式进程的用户

    ```Linux
    pstree -u
    ```

## 服务管理

- 基本介绍

  服务（service）本质就是进程，但是是运行在后台的，通常都会监听某个端口，等待其它程序的情求，比（mysqld,sshd 防火墙等，因此我们又称为守护进程（+d），是 Linux 中非常重要的知识点。daemon

- 查看服务名

  1. 使用 setup -> 系统服务就可以看到全部

  2. /etc/init.d 看到 service 指令管理的服务

     `Is -l /etc/init.d`

- service 管理指令
  1. service 服务名 [ start | stop | restart | reload | status ]
  2. 在 CentoS7.0 后很多不用 service，而是 systemctl
  3. service 指令管理的服务在 /etc/init.d 查看

- service 管理指令应用案例

  

![image-20220715124237008](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715124237008.png)

- 运行级别

  Linux 系统有 7 种运行级别（runlevel）：常用的界别 3 和 5
  运行级别 0：系统停机状态，系统默认运行级别不能设为 0，否则不能正常启动
  运行级别 1：单用户工作状态，root 权限，用于系统维护，禁止远程登陆
  运行级别 2：多用户状态（没有 NFS）,不支持网络
  运行级别 3：完全的多用户状态（有 NFS），登陆后进入控制台命令行模式
  运行级别4：系统未使用，保留
  运行级别5：X11 控制台，登陆后进入图形 GUI 模式
  运行级别6：系统正常关闭并重启，默认运行级别不能设为 6，否则不能正常启动

  开机的流程：

  ![image-20220715124928308](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715124928308.png)

  ![image-20220715125006165](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715125006165.png)

  - chkconfig 指令

    --完整单词

    -缩写字母

    - 基本介绍

      1. 通过 chkconfig 命令可以给服务的各个运行级别设置自启动/关闭

      2. chkconfig 指令管理的服务在 /etc/init.d 查看

         Centos7.0后，很多服务使用 systemct 管理

    - 基本语法

      `chkconfig`默认与`chkconfig --list`一致

      查看服务

      ```Linux
      chkconfig --list [| grep XXX]
      ```

      ![image-20220715125946814](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715125946814.png)

    - systemctl 指令

    - 

    - systemctl enable/disable 默认包括了 3 5运行级别

      ![image-20220715130433831](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715130433831.png)

      ![image-20220715132018341](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715132018341.png)

    - firewall 指令

      - 基本介绍

        在真正的生产环境，往往需要将防火墙打开，但问题来了，如果我们把防火墙打开，那么外部请求数据包就不能跟服务器监听端口通讯。这时，需要打开指定的端口。比如80、22、8080等。

        netstat -anp | more    查看端口

      - 基本用法

        ```Linux
        ```

        

      - 应用案例

      ![image-20220715132838227](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715132838227.png)



## 动态监控进程

- 基本介绍

  top 与 ps 命令很相似。它们都用来显示正在执行的进程。Top与 ps 最大的不同之处，在于 top 在执行一段时间可以更新正在运行的的进程。

- 基本语法

  ```Linux
  top [选项]
  ```

- 常用选项

  | 选项 | 全称 | 描述 |
  | :--: | :--: | :--: |
  |  -d  |      |      |
  |  -i  |      |      |
  |  -p  |      |      |

- 

  ![image-20220715133902806](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715133902806.png)

- ![image-20220715133211292](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715133211292.png)

  当前时间 up Linux 系统运行时间 系统用户数 load average 负载均衡（负载值， 和/3>0.7 负载大 ）

- Tass 系统任务数 zobie僵死

- %cpu 用户占用 系统占用 空闲 idel

- 内存占用情况：

- swap 分区

- ![image-20220715133115680](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715133115680.png)

- 交互操作

  | 操作 | 全称 | 描述 |
  | :--: | :--: | :--: |
  |  P   |      |      |
  |  M   |      |      |
  |  N   |      |      |
  |  q   | quit |      |

- 应用案例

  案例1：

  ```Linux
  top
  u username
  ```

  案例2：终止指定

  ```Linux
  top
  k pid
  ```

  ![image-20220715134700795](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715134700795.png)

## 监控网络状态

- 基本介绍

  netstat 指令查看系统网络情况

- 基本语法

  ```Linux
  netstat [选项]
  ```

  ![image-20220715134820593](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715134820593.png)

  网络协议 本地地址 外部地址

- 常用选项

  | 选项 | 全称 | 描述 |
  | :--: | :--: | :--: |
  | -an  |      |      |
  |  -p  |      |      |
  |      |      |      |

- 应用案例

  ![image-20220715140233311](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715140233311.png)



# rpm 与 yum

- 基本介绍

  ![image-20220715140401123](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715140401123.png)

- rpm 包的简单查询指令

  ![image-20220715140438901](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715140438901.png)

- rpm 包名基本格式

  ![image-20220715140857890](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715140857890.png)

- rpm 包的其他查询指令

  ![image-20220715141141447](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715141141447.png)

  - 卸载 rpm 包

    ![image-20220715141405296](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715141405296.png)

  - 安装 rpm 包

    ![image-20220715141607285](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715141607285.png)

    ![image-20220715142456915](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715142456915.png)

    - yum

      ![image-20220715143155617](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715143155617.png)

# Shell 编程

1. Linux 运维工程师在进行服务器集群管理时，需要编写 Shell 程序来进行服务器管理。
2. 对于 JavaEE 和 Python 程序员来说，工作的需要，你的老大会要求你编写一些 Shell 脚本进行程序或者是服务器的维护，比如编写一个定时备份数据库的脚本。
3. 对于大数据程序员来说，需要编写 Shell 程序来管理集群。

- 基本介绍

  Shll 是一个命令行解释器，它为用户提供了一个向 Linux 内核发送请求以便运行程序的界面系统级程序，用户可以用 Shell 来启动、挂起、停止甚至是编写一些程序。

- 脚本格式要求

  1. 脚本以 #!/bin/bash 开头

  2. 脚本需要有可执行权限

     vim /home/Hello.sh

     #!/bin/bash

     encho Hello World!

- 脚本的常用执行方式

  1. 输入脚本的绝对路径或相对路径
     首先要赋予 hello.sh 脚本可执行权限，再执行脚本
  2. 不用赋予脚本+x权限，直接执行即可
     sh hello.sh，也可以使用绝对路径

## Shell 变量

- 基本介绍

1. Linux Shell 中的变量分为，系统变量和用户自定义变量。
2. 系统变量：$HOME、$PWD、$SHELL、$USER 等等，比如：echo $HOME 等等。
3. 显示当前 shell 中所有变量：set

- Shell 变量的定义

1. 定义变量：变量名 = 值

2. 撤销变量：unset 变量

3. 声明静态变量：readonly 变量，注意：不能 unset

   ![image-20220715150338219](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715150338219.png)

- Shell 变量的规则

1. 变量名称可以由字母、数字和下划线组成，但是不能以数字开头。5A=200(×)
2. 等号两侧不能有空格
3. 变量名称一般习惯为大写

- 将命令的返回值赋值给变量

1. A= `date`反引号，运行里面的命令，并把结果返回给变量A
2. A=$(date)等价于反引号

- 设置环境变量

  - 基本语法

    1. 将 Shell 变量输出为环境变量/全局变量)

       ```Linux
       export 变量名=变量值
       ```

    2. 让修改后的配置信息立即生效

       ```Linux
       source /etc/profile
       ```

    3. 查询环境变量的值

       ```Linux
       echo $变量名
       ```

  - 应用案例

    1. 在 /etc/profile 文件中定义 TOMCAT_HOME 环境变量

    
    ![image-20220715155236119](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715155236119.png)
    
    查看环境变量TOMCAT HOME的值
    
    3.
    
    在另外一个shell程序中使用TOMCAT HOME
    
    注意：在输出TOMCAT_HOME环境变量前，需要让其生效
    
    source /etc/profile
    
    o Sh

![image-20220715155120631](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715155120631.png)

- 位置参数变量

  ![image-20220715155705525](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715155705525.png)

  \#!/bin/bash                                                                              

  echo "1=$1 2=$2 3=$3"                                                                    

  echo "所 有 的 参 数 ： "                                                                      

  echo "$@"                                                                                

  echo "参 数 个 数 ： $#"          

  vim 03_localvi.sh  100 200 444

  1=100 2=200 3=444                                                                        

  所 有 的 参 数 ：                                                                              

  100 200 444                                                                              

  参 数 个 数 ： 3 
  
  
  
  

- 预定义变量

  ![image-20220715160817982](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715160817982.png)

![](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715161221362.png)

![image-20220715161256519](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715161256519.png)

## 运算符

- 基本介绍

  学习如何在shell中进行各种运算操作

- 基本语法

- expression

  1. "$（运算式）”或“$[运算式]”或者epr m + n
  2. 注意 expr 运算符间要有空格，如果希望将 expr 的结果赋给某个变量，使用``
  3. expr m - n
  4. expr \* / % 乘，除，取余

- 应用案例

  - 案例1：计算（2 + 3） * 4 的值

    ```shell
    #!/bin/bash
    #方法 1
    Result1=$(((2+3)*4))
    echo "$Result1"
    #方法 2
    Result2=$[(2+3)*4]
    echo "$Result2"
    #方法 3
    Temp=`expr 2 + 3`
    Result3=`expr $Temp \* 4`
    echo "$Result3"                 
    ```

  - 案例2：请求出命令行的两个参数【整数】的和 20 50

    ```shell
    SUM=$[$1+$2]
    echo "$SUM"
    ```

## 条件判断

- 基本语法

  ![image-20220715163443671](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715163443671.png)

- 判断语句

  ![image-20220715165341869](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715165341869.png)

  

  ```shell
  #!/bin/bash
  if [ "ok" = "ok" ]
  then
          echo "相等"
  fi
  
  
  if [ 23 -gt 20 ]
  then
          echo "相等"
  fi
  
  
  if [ -f /root/ahs.txt ]
  then
          echo "存在"
  fi
  
  ```

- 流程控制

  ![image-20220715165803858](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220715165803858.png)

  ```shell
  #!/bin/bash
  if [ $1 -ge 60 ]
  then
          echo "及格"
  elif [ $1 -lt 60 ]
  then
          echo "不及格"
  fi
  ```

  - case 语句

    ![image-20220716124955559](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716124955559.png)
    
    ```shell
    #!/bin/bash
    case $1 in
    "1")
    echo "周一";;
    "2")
    echo "周二";;
    *)
    echo "其他";;
    esac
    ```
    
  - for 循环
  
    ![image-20220716125823932](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716125823932.png)
  
    ```shell
    #!/bin/bash
    for i in "$*"
    do
            echo "num is $i"
    done
    
    echo "==========="
    
    for q in "$@"
    do
            echo "num is $q"
    done
    ```
  
    ```shell
    #!/bin/bash
    #定义变量
    SUM=0
    for(( i=1;i<=100;i++ ))
    do
            SUM=$[$SUM+$i]
            echo $SUM
    done
    ```
  
  - while 循环
  
    ![image-20220716131220700](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716131220700.png)
  
    ```shell
    #!/bin/bash
    #!/bin/bash
    SUM=0
    q=0
    while [ $q -le $1 ]
    do
            SUM=$[$SUM+$q]
            q=$[$q+1]       
    done
    echo "执行结果是$SUM"                           
    ```
  
    - read 获取输入
  
      ![image-20220716131858316](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716131858316.png)
  
      ```shell
      #!/bin/bash
      read -p "请输入一个数NUM1=" NUM1
      echo "NUM1=$NUM1"
      ```
  
      ```shell
      #!/bin/bash
      read -t 5 -p "五秒钟等待，请输入一个数NUM2=" NUM2
      echo "NUM2=$NUM2"
      ```
  

## 函数

- 基本介绍

  ![image-20220716132657679](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716132657679.png)

- 系统函数

  

- 应用案例

  ```shell
  ```

  ![image-20220716132851077](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716132851077.png)

- 自定义函数

  ```shell
    1 #!/bin/bash
    2 #函数定义
    3 function main() {
    4         SUM=$[$N1+$N2]
    5         echo "SUM=$SUM"
    6 }
    7 
    8 #输入两个值
    9 read -p "请输入N1=" $N1
   10 read -p "请输入N2=" $N2
  ```

  ![image-20220716140259536](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716140259536.png)

- ![image-20220716140338631](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716140338631.png)

# 乌班图

# 日志

- 基本介绍

  1. 日志文件是重要的系统信息文件，其中记录了许多重要的系统事件，包括用户的登录信息、系统的启动信息、系统的安全信息、邮件相关信息、各种服务相关信息等。

  2. 日志对于安全来说，它记录了系统每天发生的各种事情，通过日志来检查错误发生的原因或者受到攻击时攻击者留下的痕迹。

  3. 可以这样理解日志是用来记录重大事件的工具

     **/var/log**

- 系统常用日志

  ![image-20220716141340175](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716141340175.png)

- 应用案例

  ![image-20220716141934823](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716141934823.png)

## 日志管理服务 rsyslogd

![image-20220716142823611](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716142823611.png)

![image-20220716142838819](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716142838819.png)

![image-20220716143025932](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716143025932.png)

![image-20220716143218460](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716143218460.png)

事件发生的时间 事件发生的主机 事件发生的程序/服务 时间的描述

![image-20220716143535786](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716143535786.png)

![image-20220716144120544](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716144120544.png)

## 日志轮替

- 基本介绍

- 日志轮替文件命名

  ![image-20220716145021149](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716145021149.png)

  ![image-20220716145401876](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716145401876.png)

![image-20220716145947542](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716145947542.png)

![image-20220716150050233](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716150050233.png)

![image-20220716150214181](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716150214181.png)

![image-20220716150306597](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716150306597.png)

## 内存日志

![image-20220716150500245](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716150500245.png)

# 定制 Linux

通过裁剪现有 Linux系统 (CentOS7.6),创建属于自己的min Linux小系统，可以加深我们对linux的理解。

- 启动流程介绍

![image-20220716150731035](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716150731035.png)

# Linux 内核源码

# Linux 备份与恢复

![image-20220716151028640](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716151028640.png)

![image-20220716151116805](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716151116805.png)

## dump 

![image-20220716151250417](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716151250417.png)

![image-20220716160353034](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716160353034.png)

- 应用案例

  ![image-20220716160550099](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716160550099.png)

  - 案例1：

    ```shell
    
    ```

  - 案例2：

    ```shell
    restore
    ```

  

  ## restore

  - 基本介绍
  - 基本语法
  - 常用选项

  ![image-20220716160634361](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716160634361.png)

  - 应用案例

    ![image-20220716160825556](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716160825556.png)

    ![image-20220716160857864](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716160857864.png)

  

# 可视化管理工具

## webmin

- 基本介绍

  Webmin 是功能强大的基于 Web 的 Unix/Linux 系统管理工具。管理员通过浏览器访问 Webmin 的各种管功能并完成相应的管理操作。除了各版本的 Linux  以外还可用于：AIX、HPUX、Solaris、Unixware、Irix 和 FreeBSD 等系统。

- 安装 webmin 与配置

  1. 下载地址：
  2. 安装：
  3. 重置密码
  4. 修改 webmin 服务的端口号
  5. 重启 webmin
  6. 防火墙开放 6666 端口
  7. 登录 webmin

  ![image-20220716161201610](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716161201610.png)

  ![image-20220716161430088](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716161430088.png)

## bt 宝塔

- 基本介绍

  bt 宝塔 Linux 面板是提升运维效率的服务器管理软件，支持一键LAMP/LNMP/集群/监控/网站/FTP/数据库/JAVA等多项服务器管理功能。

- 安装和使用

  1. 分
  2. 

![image-20220716161706977](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220716161706977.png)

# 面试题

P142开始
