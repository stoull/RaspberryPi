# 在Raspberrypi上使用BitTorrent客户端


BitTorrent is a peer-to-peer (P2P) file-sharing protocol

[Install deluge on debain](https://dev.deluge-torrent.org/wiki/Installing/Linux/Debian/Jessie)

[How-to guides](https://deluge.readthedocs.io/en/latest/how-to/index.html)

[Deluge as a service](https://deluge.readthedocs.io/en/latest/how-to/systemd-service.html)

## Transmission

[transmissionbt.com](https://transmissionbt.com)
[transmission Github](https://github.com/transmission/transmission)

Transmission is a set of lightweight BitTorrent clients (in GUI, CLI and daemon form). All its incarnations feature a very simple, intuitive interface on top on an efficient, cross-platform back-end.

[transmission wiki](https://github.com/transmission/transmission/wiki)

[TransmissionHowTo](https://help.ubuntu.com/community/TransmissionHowTo)

## Deluge
[deluge-torrent.org](https://deluge-torrent.org)
### 安装
#### 安装GUI
设备为默认的程序[How to set Deluge as default torrent application](https://deluge.readthedocs.io/en/latest/how-to/set-mime-type.html)

#### 安装deluge服务
以服务的形式运行deluge，可设置随机器开关开启或停止服务，而且当deluge因错误crash停止服务后，还可以自动重启。

使用命令安装：
`sudo apt install deluged deluge-web` 或者 `apt-get install deluged deluge-web`

#### 使用 Deluge Ubuntu Launchpad PPA安装
`add-apt-repository 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu trusty main'`

### 使用
[How to create systemd services for Linux](https://deluge.readthedocs.io/en/latest/how-to/systemd-service.html)