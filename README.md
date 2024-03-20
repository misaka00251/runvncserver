# startvnc

原理：VNC 和本地都使用同一个 session，这样在插着 HDMI 输出的情况下，自动登录开启，vnc 也可以正常连接到桌面。

感谢 [runvncserver](https://github.com/sebestyenistvan/runvncserver) 项目。

## 操作

0. 需要系统内安装 tigervnc

```
sudo dnf install tigervnc-server
```

1. xfce4 + lightdm 的搭配，前提保证 `/etc/lightdm/lightdm.conf` 内开启了自动登录。

```
autologin-user=openeuler
autologin-user-timeout=0
```

2. 将 startvnc 放到 `/usr/local/bin` 下面，然后加上执行权限。

```
sudo chmod +x /usr/local/bin/startvnc
```

3. 创建 `/etc/systemd/system/vnc.service`，并开机启动，原 vncservice@x.service 禁用。

```
sudo systemctl enable vnc.service
```

4. 重启即可
