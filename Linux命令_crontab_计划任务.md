# Linux 计划任务 `Cron`

Truble Shoot:

1. [Why is my crontab not working, and how can I troubleshoot it?](https://serverfault.com/questions/449651/why-is-my-crontab-not-working-and-how-can-i-troubleshoot-it?newreg=1345265e1c3840a7a26181bd227f9fc5)

2. 注意脚本中的相对路径及绝对路径，如果在脚本中使用的了 cat >> ./xxxlog.txt 其中的.表示为/home/pi/路径

`crontab`(cron table)命令用来编辑当前定时任务列表，并且是针对用户的，每一个用户（包括root）都有一个自己的定时计划任务列表。

### 编辑计划任务列表

	crontab -e

`sudo su -`

>
如果出现问题`crontab: no crontab for jjmay - using an empty one`
使用root权限为用户设置：
`crontab -u <user_name> -e`
`sudo su <user_name>`
	
首次运行`crontab`的时候，会提示选择编辑器，如不确定选择哪一个，按`Enter`键选择`nano`


```
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
~                             
```
	
### 增加计划任务

计划任务列表中的一条记录，最多由六部分组成：

`# m h  dom mon dow   command`

```
# * * * * *  command to execute
# ┬ ┬ ┬ ┬ ┬
# │ │ │ │ │
# │ │ │ │ │
# │ │ │ │ └───── day of week (0 - 7) (0 to 6 are Sunday to Saturday, or use names; 7 is Sunday, the same as 0)
# │ │ │ └────────── month (1 - 12)
# │ │ └─────────────── day of month (1 - 31)
# │ └──────────────────── hour (0 - 23)
# └───────────────────────── min (0 - 59)
```

```
*	any value
,	value list separator
-	range of values
/	step values
@yearly	(non-standard)
@annually	(non-standard)
@monthly	(non-standard)
@weekly	(non-standard)
@daily	(non-standard)
@hourly	(non-standard)
@reboot	(non-standard)
```

`/`: step values
如：

`*/3 * * * *` 为每三分钟

`* */30 * * *` ：At every minute past every 3rd hour

`0 */3 * * *` : At minute 0 past every 3rd hour

例如：

`0 0 * * *  /home/pi/backup.sh`

这一条计划任务会在每天晚上0点运行`backup.sh`

每个星期天5 am进行所有用户的备份：
`0 5 * * 1 tar -zcf /var/backups/home.tgz /home/`

每30分钟请求一个地址：
`0 */10 * * * /usr/bin/curl http://www.google.com/`

每分钟运行：
`*/1 * * * * /home/local/test.sh`

在凌晨00:10运行
`10 0 * * * /home/swz/aa.sh`

// 句式生成器
[crontab guru](https://crontab.guru/#*_*/30_*_*_*)

### 查看计划任务

`crontab -l`

将会列出当前保存的计划任务

### 清空计划任务

`crontab -r`
将删除当前保存的所有计划任务

**主要命令:**

```
crontab –e     //修改 crontab 文件，如果文件不存在会自动创建。 
crontab –l      //显示 crontab 文件。 
crontab -r      //删除 crontab 文件。
crontab -ir     //删除 crontab 文件前提醒用户。

service cron status     //查看crontab服务状态
service cron start     //启动服务 
service cron stop     //关闭服务 
service cron restart     //重启服务 
service cron reload     //重新载入配置
```

### 运行系统启动时的运行任务
当要设置在开机启动时的任务，用`@reboot`,而不是设置具体的时间
` @reboot python /home/pi/myscript.py` 
`myscript.py `将会在开机的时候运行。

如果想如计划的任务在后台运行，不影响系统启动，可在命令后面增加`&`
` @reboot python /home/pi/myscript.py &`

### 设置开机启动时的运行任务 The systemd Daemon
想在开机启动时运行命令或程序，可以以增加系统服务的形式实现。而且一旦增加了一个服务，用户可对服务进行 停止/开始， 停用/启用 等操作

#### 创建一个服务
服务文件名是后缀为`. service`的文件， 比如一个自定服务的文件名为`myscript.service`。文件内容如下：

>
>```
[Unit]
Description=My service
After=network.target

>[Service]
ExecStart=/usr/bin/python3 -u main.py
WorkingDirectory=/home/pi/myscript
StandardOutput=inherit
StandardError=inherit
Restart=always
User=pi

>[Install]
WantedBy=multi-user.target
```
这个文件会在目录`WorkingDirectory `下运行命令`/usr/bin/python3 -u main.py`。当然可以替换成其它想在系统启动事件时运行的命令。

将这个文件使用root权限复制到目录`/etc/systemd/system `，如：

`sudo cp myscript.service /etc/systemd/system/myscript.service`

复制之后，通知系统添加了新服务，进行更新：

`sudo systemctl daemon-reload`

系统更新服务之后，就可以对这个服务进行操作：

运行服务：
`sudo systemctl start myscript.service`

停止服务：
`sudo systemctl stop myscript.service`

当你确定这个服务没有问题之后，可设置此服务为开机运行：

`sudo systemctl enable myscript.service`

`systemctl `命令还可以用于重启或停用相应的服务，在macOS上是`launchctl`命令

**注意**
> 服务运行时机是可以设置的，上面的例子是在启动后比较晚的时机运行的（当网络可用之后`After=network.target`）, 可根据需要设置其它的时机。

