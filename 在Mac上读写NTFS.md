# Mac上读写NTFS


## 使用macFUSE
1. 下载并安装最新的mac版FUSE [http://osxfuse.github.io. ](http://osxfuse.github.io)
这个步骤需要重启mac，安装后打开设置app, 在最底部可以找到`macFUSE`

2. 使用HomeBrew 安装 `NTFS-3G`
>`brew tap gromgit/homebrew-fuse`
`brew install ntfs-3g-mac`

3. 手动挂载NTFS. **注意：将disk4s2更换为对应的分区**
> 1. 使用`diskutil list`查看分区信息
> 2. 如果NTFS磁盘已被系统自动挂载，先卸载对应的磁盘分区
> `sudo diskutil unmount /dev/disk4s2`
> 3. 新建一个目录用来挂载磁盘
> `sudo mkdir /Volumes/NTFS`
> 4. 以读写模式挂载NTFS 磁盘
> `sudo /usr/local/bin/ntfs-3g /dev/disk1s1 /Volumes/NTFS -o local -o allow_other -o auto_xattr -o auto_cache`
> 或者 `sudo /usr/local/sbin/mount_ntfs /dev/disk4s2 /Volumes/NTFS`

这样就会挂载一个名为NTFS的磁盘，可进行读写操作，使用`mount`查看对应的信息为：
`/dev/disk4s2 on /Volumes/NTFS (macfuse, local, synchronous, noatime)`

4. 卸载
`sudo diskutil unmount /dev/disk4s2`