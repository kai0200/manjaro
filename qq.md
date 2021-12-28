# 02 - Manjaro下安装QQ 、WeChat
spark 版本比较稳定，但是升级（2021-12-21）后,"yay -Ss com.qq.weixin.spark" 显示“过时”， com.qq.weixin.deepin测试可用。

## 安装字体
```
# 安装字体
# 下载一个 msyh.ttf

cp -rf msyh.ttf  ~/.deepinwine/Spark-TIM/drive_c/windows/Fonts/

sudo pacman -S wqy-microhei wqy-bitmapfont wqy-zenhei wqy-microhei-lite ttf-dejavu noto-fonts noto-fonts-extra noto-fonts-emoji noto-fonts-cjk

fc-cache -fv
```


## TIM
```
yay -S com.qq.tim.spark
```

## 调整字体 显示-> DPI -> 192 (默认96×2)
```
env WINEPREFIX="$HOME/.deepinwine/Spark-TIM" deepin-wine5 winecfg
```

## WeChat 安装
这里感觉上com.qq.weixin.deepin整合做的比较好，基本安装完毕不需要调整。
```
yay -S com.qq.weixin.deepin
```

## 调整WeChat字体大小 192
```
env WINEPREFIX="$HOME/.deepinwine/Deepin-WeChat/" /usr/bin/deepin-wine6-stable winecfg
```

## wechat输入显示方框
```
系统语言非中文时，中文全显示成方块，需要在

/opt/deepinwine/tools/run.sh

中将 WINE_CMD 那一行修改为

WINE_CMD="LC_ALL=zh_CN.UTF-8 deepin-wine"
```

## TIM(QQ) 标题框显示白框
应该是字体库没有装全，等安装玩wps再看一下，
如果还出现空子符框，拷贝字体目录省事了。
```
find /usr/share/fonts -name 'msyh.*' # 发现有msyh字体
# 拷贝字体后解决
cp /usr/share/fonts/vista/Fonts/* ~/.deepinwine/Spark-TIM/drive_c/windows/Fonts/

# 重启机器
systemctl reboot
```

## Tim卡顿现象尝试gnome
卡顿现象还是有搜了几次暂时先按以下配置操作。
Manjaro-kde桌面安装TIM/QQ的时候经常出现无法启动，其主要原因是deein-wine-tim打包了Gnome桌面部分内容，因此在KDE桌面环境下需要安装相应的Gnome桌面设置环境
```
yay -S gnome-settings-daemon
cp /etc/xdg/autostart/org.gnome.SettingsDaemon.XSettings.desktop ~/.config/autostart

chmod +x ~/.config/autostart/org.gnome.SettingsDaemon.XSettings.desktop
kill /usr/bin/xsettingsd

# 增加开机启动，保证Tim不卡顿
echo "/usr/lib/gsd-xsettings &" >> ~/.xinitrc
```
