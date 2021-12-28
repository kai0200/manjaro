# nuc11 install manjaro-i3-mini

## 默认的配置
刚装完启动以后发现如果自己定义了.i3/config 之前的配置就没有了，好奇这配置在什么地方。
第一现场装完以后启动sshd，用户顺手的机器登录操作（默认这个终端真是太丑了）
```
systemctl enable sshd
systemctl start sshd
```
### Pacman.conf
pacman使用 安装了系统时候, 应该立马使用pacman-mirrors -c China更新源, 
再使用pacman -Syyn 更新系统
编辑/etc/pacman.conf添加

[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch

pacman -Sy 更新数据库, 类似于yum reoplist
pacman -S archlinuxcn-keyring 下载key

### Xmodmap 修改键盘
cp Xmodmap .Xmodmap

### default i3 config
~/.i3   # 误会为.config/i3了

### DPI terminal
add following lines to ~/.Xresources and run xrdb ~/.Xresources
```
$ vim ~/.Xresources

Xft.dpi:       192
rofi.dpi:      192
*.dpi:         192


$ systemctl reboot
```

### conky
conky -c /usr/share/conky/conky1.10_shortcuts_maia
conky -c /usr/share/conky/conky_maia

### pacman
sudo pacman -Syu

### alacritty
sudo pacman -S alacritty



