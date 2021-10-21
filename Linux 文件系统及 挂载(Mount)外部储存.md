# Linux 文件系统及 挂载(Mount)外部储存

### 磁盘在linux系统中的表示方法：
硬盘为IDE接口类型 hda dhb： hda1 hda2 hda3...
硬盘为 SATA接口，SCIS接口，USB: sda, sdb, sda1, sda2...

所有磁盘设备及分区都以文件的形式存储在/dev/,但是这些文件不能直接使用，如果要往这些分区内写入数据就需要挂载分区。
所谓的挂载点就是文件系统中存在的一个目录，通常情况下，创建在/mnt目录下，挂载成功后，访问挂载点就是访问新的存储设备。



[鸟哥私房菜 - 7.1 认识 Linux 文件系统](https://wizardforcel.gitbooks.io/vbird-linux-basic-4e/content/59.html)

[一口气搞懂「文件系统」，就靠这 25 张图了](https://segmentfault.com/a/1190000023615225)

[Linux文件系统简介&挂载简介](https://blog.csdn.net/zhangpower1993/article/details/52213030)
[什么是挂载，Linux挂载如何实现详解](https://www.cnblogs.com/cangqinglang/p/12170828.html)
[What is a Mount?](https://www.computerhope.com/jargon/m/mount.htm)
[What is meant by mounting a drive?](https://kb.iu.edu/d/anqk)