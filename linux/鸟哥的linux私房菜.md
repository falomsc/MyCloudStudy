#### 第五章，首次登陆与在线求助man page

1. 基础命令的操作

   ```shell
   date
   date +%Y/%m/%d
   date +%H:%M
   cal
   cal 2009
   cal 10 2009
   bc
   10/100
   quit
   bc
   scale=3
   ```

   

2. 123

#### 第六章，Linux的文件权限与目录配置

1. Linux的文件属性

   ```shell
   [root@localhost ~]# ls -al
   total 36
   dr-xr-x---.  5 root root  225 Apr 11 08:45 .
   dr-xr-xr-x. 17 root root  224 Apr  9 20:09 ..
   -rw-------.  1 root root 2073 Apr  9 20:10 anaconda-ks.cfg
   -rw-------.  1 root root   77 Apr  9 21:56 .bash_history
   -rw-r--r--.  1 root root   18 Dec 28  2013 .bash_logout
   -rw-r--r--.  1 root root  176 Dec 28  2013 .bash_profile
   -rw-r--r--.  1 root root  176 Dec 28  2013 .bashrc
   drwx------.  4 root root   31 Apr  9 21:55 .cache
   drwx------.  4 root root   30 Apr  9 21:55 .config
   -rw-r--r--.  1 root root  100 Dec 28  2013 .cshrc
   drwx------.  3 root root   25 Apr  9 20:10 .dbus
   -rw-r--r--.  1 root root 2121 Apr  9 20:21 initial-setup-ks.cfg
   -rw-r--r--.  1 root root  129 Dec 28  2013 .tcshrc
   -rw-------.  1 root root   67 Apr 11 08:45 .xauthumki6z
   ```

   第一列代表文件的类型与权限。d是目录，-是文件，l是连接文件，b是设备文件里可供存储的接口设备，c是设备文件里的串行接口设备

   接下来的字符中，以3个为一组，且均为“rwx”的3个参数的组合。r代表可读，w代表可写，x代表可执行，-代表没有权限。第一组为文件所有者的权限，第二组为同用户组的权限，第三组为其他非本用户组的权限

   第二列表示有多少文件名连接到此节点

   第三列表示这个文件或目录的所有者账号

   第四列表示这个文件的所属用户组

   第五列为这个文件的容量大小，默认单位为B

   第六类为这个文件的创建文件日期或者是最近的修改日期

   第七列为该文件名

   

2. 如何改变文件属性与权限

   改变所属用户组

   ```shell
   chgrp users install.log
   ```

   改变文件所有者

   ```shell
   chown bin install.log
   chown root:root install.log
   ```

   改变权限

   各权限的分数为：r：4，w：2，x：1

   ```shell
   chmod 777 .bashrc
   ```

   另外一种改变权限的方法

   ```shell
   chmod u=rwx,go=rx .bashrc
   ```

   

3. 234