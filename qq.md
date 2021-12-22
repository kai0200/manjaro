# QQ WeChat安装
spark 版本比较稳定，但是升级（2021-12-21）后spark版本wechat显示“过时”，安装com.qq.weixin.deepin测试可用。

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

## 调整字体 显示-> DPI -> 196
```
env WINEPREFIX="$$$HOME/.deepinwine/Spark-TIM" deepin-wine5 winecfg
```

## WeChat 安装
```
yay -S com.qq.weixin.deepin
```

## 调整WeChat字体大小 196
```
env WINEPREFIX="$$$HOME/.deepinwine/Deepin-WeChat/" /usr/bin/deepin-wine6-stable winecfg
```

## TIM(腾讯QQ) 标题框显示白框
出现空子符框，没有仔细研究，拷贝个字体省事了。
```
find /usr/share/fonts -name 'msyh.*' # 发现有msyh字体
# 拷贝字体后解决
cp /usr/share/fonts/vista/Fonts/* ~/.deepinwine/Spark-TIM/drive_c/windows/Fonts/
```

## Tim卡顿现象尝试gnome
```
Manjaro-kde桌面安装TIM/QQ的时候经常出现无法启动，其主要原因是deein-wine-tim打包了Gnome桌面部分内容，因此在KDE桌面环境下需要安装相应的Gnome桌面设置环境
yay -S gnome-settings-daemon
cp /etc/xdg/autostart/org.gnome.SettingsDaemon.XSettings.desktop ~/.config/autostart

chmod +x ~/.config/autostart/org.gnome.SettingsDaemon.XSettings.desktop
kill /usr/bin/xsettingsd

# 增加开机启动，保证Tim不卡顿
echo "/usr/lib/gsd-xsettings &" >> ~/.xinitrc 
```

```
#备注一个注册表生效方法, 无需操作
cd ~/.deepinwine/Spark-TIM
env WINEPREFIX="$$$HOME/.deepinwine/Spark-TIM/" deepin-wine5 regedit msyh_config.reg
```
