# 常用软件

## DD 制作启动U盘

```sh
ls -l /dev/disk/by-id/|grep usb# 检查插入的U盘
/dev/sdx # 找到设备
sudo dd if=manjaro.iso of=/dev/sdX bs=1M oflag=sync status=progress
```

## 安装网卡驱动
```
默认安装后无法驱动无线网卡驱动，此是可以使用安卓手机的USB共享网络功能连接网络操作安装网卡驱动
[参考 https://www.jianshu.com/p/21667171d2b1]
博通4360这个网卡一般是mac上的网卡
lspci -vnn |grep 0280 # 应该能看到BCM4360关键字
pacman -S broadcom-wl-dkms  # 如果提示缺少linux内核
#pacman -S linux-header  # 安装内核
#uname -an # 安装制定内核
#git clone https://github.com/antoineco/broadcom-wl.git
#sudo dkms add -m broadcom-wl -v 6.30.223.271
sudo pacman -S linux # 最后一步更新内核后重新启动
```

## manjaro 改键
```
xev
xmodmap .Xmodmap
现有问题fn键盘扩展功能？
```

## 1. 搜狗输入法
```
sudo pacman -Sy fcitx
sudo pacman -Sy fcitx-configtool
yay fcitx-sogoupinyin
yay fcitx-qt4
# 以上四步是fcitx和搜狗拼音的配置

sudo echo -e "export GTK_IM_MODULE=fcitx\nexport QT_IM_MODULE=fcitx\nexport XMODIFIERS=@im=fcitx">>~/.xprofile
```

## 2. WPS
```
yay -S wps-office-mui-zh-cn wps-office-mime-cn wps-office-cn wps-office-fonts ttf-ms-fonts  ttf-wps-fonts --overwrite "*"
```

## 3. git
```
yay -S git
yay -S gitkraken
```

## 4. 其他常用软件
```
pacman -S net-tools # ifconfig
yay -S mpv #视频播放器
yay -S vlc #视频播放器
yay -S netease-cloud-music #网易云音乐
yay -S gimp #图像编辑器
yay -S redshift #红移
yay -S haroopad #markdown编辑器
yay -S Typora #markdown编辑器
yay -S freeMind #思维图
yay -S pspp #spss
yay -S uget #下载工具
yay -S qbittorrent #BT下载
yay -S zotero #文献管理软件
yay -S filezilla  #FTP工具
yay -S filelight #磁盘使用空间
yay -S baobab #磁盘使用情况分析器
yay -S hardinfo #硬件检测工具
yay -S acroread #pdf阅读
yay -S pdfsam #pdf编辑
yay -S masterpdfeditor  #pdf阅读编辑
yay -S neofetch # shell display title
yay -S translate-shell #命令行翻译
```

## 5. deepin 包支持
```
 1) deepin-account-faces  2) deepin-anything  3) deepin-api
 4) deepin-calendar  5) deepin-control-center  6) deepin-daemon
 7) deepin-desktop-base  8) deepin-desktop-schemas  9) deepin-dock
 10) deepin-file-manager  11) deepin-gtk-theme  12) deepin-image-viewer
 13) deepin-launcher  14) deepin-manual  15) deepin-menu
 16) deepin-network-utils  17) deepin-polkit-agent-ext-gnomekeyring
 18) deepin-qt5dxcb-plugin  19) deepin-qt5integration  20) deepin-screensaver
 21) deepin-session-ui  22) deepin-shortcut-viewer  23) deepin-sound-theme
 24) deepin-system-monitor  25) deepin-turbo  26) startdde
yay -s deepin-wine
yay -S deepin-wxwork  #企业微信 
yay -S deepin-wine-wechat #微信
yay -S deepin-qq-eim  #QQ
yay -S deepin-baidu-pan #百度网盘
yay -S deepin-wine-tim #TIM
yay -S deepin-screenshot #截屏软件
###另外：安装QQ 可以参考[https://aur.archlinux.org/packages/deepin.com.qq.office/]
yay -S deepin.com.qq.office  ##TIM
yay -S deepin.com.qq.im  ## QQ
```

## 6. deb包安装
```
yay -S debtap #安装包
sudo debtap -u #升级
sudo debtap xxxx.deb #解压
#debtap -q xxx.deb #静默解压
sudo pacman -U x.tar.xz #安装
```

## 7. nc
```
sudo pacman -S nmap
sudo ln -s /usr/bin/ncat /usr/bin/nc
```

## 8. tar.xz
```
sudo pacman -U x.tar.xz
```

## 9. QQ
```
yay -S com.qq.tim.spark
env WINEPREFIX="$HOME/.deepinwine/Spark-TIM" deepin-wine5 winecfg # 修改96为192
ln -s /usr/share/fonts/vista    /home/$USER/.deepinwine/Spark-TIM/drive_c/windows/Fonts/
```

## 10. wechat
```
yay -S com.qq.weixin.deepin
run.sh 中设置
GDK_BACKEND=x11 lxappearance
env WINEPREFIX="$HOME/.deepinwine/Deepin-WeChat/" /usr/bin/deepin-wine6-stable winecfg
ln -s /usr/share/fonts/vista    /home/$USER/.deepinwine/Deepin-WeChat/drive_c/windows/Fonts/
```
## 11. 字体安装

## 12. nc
```
sudo pacman -S nmap
```

## 13. 壁纸
```
sudo pacman -S variety
点击 Add 
wallhaven 选择好屏幕分辨率，复制链接粘贴到Add
```
## 14. nvim
```
sudo pacman -S neovim
curl -sLf https://spacevim.org/cn/install.sh | bash
python3 -m pip install pynvim
pacman -S nodejs npm
/home/caler/.SpaceVim
git checkout v1.7.0
```

## 15. fish

## 16. 音量、屏幕亮度
```
yay -S acpilight 
sudo gpasswd video -a $USER #加入video组免密码
# echo 200 | sudo tee /sys/class/backlight/intel_backlight/brightness
sudo chmod +007 /sys/class/backlight/intel_backlight/brightness
xbacklight -dec 50
xbacklight -inc 50

# 屏幕亮度
bindsym XF86MonBrightnessUp exec "xbacklight -inc 10; notify-send 'brightness up'"
bindsym XF86MonBrightnessDown exec "xbacklight -dec 10; notify-send 'brightness down'"
# macbook F1 默认是功能键盘，fn+F1是F1

# 声音大小
bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ +10% && $refresh_i3status
bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ -10% && $refresh_i3status
bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute @DEFAULT_SINK@ toggle && $refresh_i3status
bindsym XF86AudioMicMute exec --no-startup-id pactl set-source-mute @DEFAULT_SOURCE@ toggle && $refresh_i3status
```

## 17. ranger 
```
set -gx EDITOR nvim
add into .config/fish/config.fish
```
