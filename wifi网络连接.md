# wifi 网络连接

[使用wpa_cli](https://wiki.archlinux.org/title/Wpa_supplicant_(简体中文))

因为学习的原因，我的pi要在我的工作地点和家里频繁移动，这样我希望我的pi当我到家的时候能自动接家的wifi，到办公室的时候能够自动的接入到公室的wifi。
我将`/etc/wpa_supplicant/wpa_supplicant.conf`文件中的内容更改为下面注释中的内容，就满足了我的需求。

```
country=CN
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="Tenda_DA8BB0_5G"
    psk="your_wifi_password"
    id_str="work1"
}

network={
    ssid="Tenda_DA8BB0"
    psk="your_wifi_password"
    id_str="work2"
}

network={
    ssid="CMCC-Hut"
    psk="your_wifi_password"
    id_str="home1"
}

network={
    ssid="ChangChun_iPhone"
    psk="your_wifi_password"
    id_str="phone_hotspot"
}
```

参考资料：
[Changing Wifi networks from the command line interface](https://forums.raspberrypi.com/viewtopic.php?t=179387)