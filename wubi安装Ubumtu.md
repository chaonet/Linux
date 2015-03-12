# 两种安装ubuntu、windows双系统的方法
1. U盘、CD安装:需要对硬盘进行分区，会有两个完全独立的操作系统
2. wubi安装:ubuntu可以被当做程序进行安装、卸载

# 我选择wubi的原因
1. 没钱换电脑……
2. 电脑工作要用，不敢随意折腾分区

# wubi安装需要
1. 到官网下载对应的操作系统IOS文件：[链接](http://www.ubuntu.org.cn/download/desktop)
2. 下载ISO刻录文件，比如“UltraISO”，或者直接用rar

# 安装步骤
1. 将ISO打开，单独解压“wubi.exe”
2. 将ISO文件和解压出来的“wubi.exe”放在同一个目录下
3. 断网
4. 打开命令行，切换到ISO文件所在目录
5. 输入命令：wubi.exe --32bit，（我用的是32位的系统）是两个-，注意空格，稍等几秒，弹出窗口
6. 选择ubuntu安装的盘符、分配空间大小，输入ubuntu系统的登录密码
7. 等进度条跑完，会提示立即重启还是稍后手动重启，选择稍后手动重启
8. 重启后，不用按任何键，会出现几秒“esc”选择时间，也不要动。然后会进入安装界面，点右上角无线标识，连上网，安装过程中系统会自动下载文件，然后就是静静地等待……
9. 系统安装完成，会自动重启，这时能看到windows和ubuntu两个选择，选择进入ubuntu
10. 出现“ubuntu”和“ubuntu高级”，进入高级
11. 不要急着进入，高亮“恢复模式”，按“E”键进入编辑模式，将“loop=/ubuntu/disks/root.disk”后面的ro改为rw,按“F10”进入编辑后的“恢复模式”
12. 选择“root”，回车，下方出现root用户的命令行界面，输入“sudo vi /etc/grub.d/10_lupin” 找到 “linux   ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_file_relative} ro ${args}”，将“${args}”前面的“ro”改为“rw”，reboot进行重启
13. 选择ubuntu系统，然后选择ubuntu，而不是"ubuntu高级"
14. 出现界面中间出现“ubuntu”图标和五个进度点，会三次提示挂载出错、磁盘未就绪等，选择忽略、跳过、跳过即可
15. 成功进入系统。

# 驱动、软件安装
1. 没有额外安装驱动，进入后无线就已经连上
2. 终端程序、文本编辑程序、python都是系统自带，不需要另外安装

# 其他
因为我安装ubuntu的分区只有32G空余空间，所以分了一半给ubuntu。进入ubuntu并安装了200+M程序更新后，一共用了4+G，剩余9+G空间。
这个安装方法主要的内容是我用google搜到的一个文章介绍的，因为有点特殊情况，略有不同，有兴趣可以看原文:[链接](http://ubuntu-with-wubi.blogspot.com/2014/10/installing-ubuntu-14041-with-wubi.html)（需翻墙）
