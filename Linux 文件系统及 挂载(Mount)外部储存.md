# Linux 文件系统及 挂载(Mount)外部储存

### 在Linux中，每个硬件设备都被当成一个文件来对待
几乎所有的硬件设备文件（硬盘及分区，打印机，蓝牙耳机）都存放在/dev目录内。常见设备的命名：

|  设备   | 在Linux内的文件名  |
|  ----  | ----  |
| SCSI/SATA/USB硬盘机  | /dev/sd[a-p] |
| VirtI/O界面  | /dev/vd[a-p] （用于虚拟机内） |
| 软盘机 | /dev/fd[0-7] | 
| 打印机 | /dev/lp[0-2] （25针打印机） /dev/usb/lp[0-15] （USB 接口） | 
| 鼠标 | /dev/input/mouse[0-15] （通用） /dev/psaux （PS/2界面） /dev/mouse （当前鼠标） | 
| CDROM/DVDROM | /dev/scd[0-1] （通用） /dev/sr[0-1] （通用，CentOS 较常见） /dev/cdrom （当前 CDROM） | 
| 磁带机 | /dev/ht0 （IDE 界面） /dev/st0 （SATA/SCSI界面） /dev/tape （当前磁带） | 
| IDE硬盘机 | /dev/hd[a-d] （旧式系统才有） | 
| 控制终端 | tty(teletype) | 

* /dev/sd[a-p][1-128]：为实体磁盘的磁盘文件名；
* /dev/vd[a-d][1-128]：为虚拟磁盘的磁盘文件名





硬盘为IDE接口类型 hda dhb： hda1 hda2 hda3...
硬盘为 SATA接口，SCIS接口，USB: sda, sdb, sda1, sda2...

所有磁盘设备及分区都以文件的形式存储在/dev/,但是这些文件不能直接使用，如果要往这些分区内写入数据就需要挂载分区。
所谓的挂载点就是文件系统中存在的一个目录，通常情况下，创建在/mnt目录下，挂载成功后，访问挂载点就是访问新的存储设备。



[7.3 磁盘的分区、格式化、检验与挂载](https://wizardforcel.gitbooks.io/vbird-linux-basic-4e/content/61.html)
[鸟哥私房菜 - 7.1 认识 Linux 文件系统](https://wizardforcel.gitbooks.io/vbird-linux-basic-4e/content/59.html)

[一口气搞懂「文件系统」，就靠这 25 张图了](https://segmentfault.com/a/1190000023615225)

[Linux文件系统简介&挂载简介](https://blog.csdn.net/zhangpower1993/article/details/52213030)
[什么是挂载，Linux挂载如何实现详解](https://www.cnblogs.com/cangqinglang/p/12170828.html)
[What is a Mount?](https://www.computerhope.com/jargon/m/mount.htm)
[What is meant by mounting a drive?](https://kb.iu.edu/d/anqk)