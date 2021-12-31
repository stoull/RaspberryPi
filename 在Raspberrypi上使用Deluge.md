# 在Raspberrypi上使用Deluge


[Install deluge on debain](https://dev.deluge-torrent.org/wiki/Installing/Linux/Debian/Jessie)



[How-to guides](https://deluge.readthedocs.io/en/latest/how-to/index.html)


[Deluge as a service](https://deluge.readthedocs.io/en/latest/how-to/systemd-service.html)

## 安装
### 安装GUI
设备为默认的程序[How to set Deluge as default torrent application](https://deluge.readthedocs.io/en/latest/how-to/set-mime-type.html)

### 安装deluge服务
以服务的形式运行deluge，可设置随机器开关开启或停止服务，而且当deluge因错误crash停止服务后，还可以自动重启。

使用命令安装：
`sudo apt install deluged deluge-web` 或者 `apt-get install deluged deluge-web`

### 使用 Deluge Ubuntu Launchpad PPA安装
`add-apt-repository 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu trusty main'`

## 使用
[How to create systemd services for Linux](https://deluge.readthedocs.io/en/latest/how-to/systemd-service.html)