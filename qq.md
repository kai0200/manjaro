# QQ WeChat安装
spark 版本比较稳定，但是升级（2021-12-21）后spark版本wechat显示“过时”，安装com.qq.weixin.deepin测试可用。

## 安装过程
```
# 安装字体
sudo pacman -S wqy-microhei wqy-bitmapfont wqy-zenhei wqy-microhei-lite ttf-dejavu noto-fonts noto-fonts-extra noto-fonts-emoji noto-fonts-cjk
fc-cache -fv

# Tim
yay -S com.qq.tim.spark

# 调整字体 显示-> DPI -> 196
env WINEPREFIX="$HOME/.deepinwine/Spark-TIM" deepin-wine5 winecfg

# WeChat
yay -S com.qq.weixin.deepin

# 调整WeChat字体大小 196
env WINEPREFIX="$HOME/.deepinwine/Deepin-WeChat/" /usr/bin/deepin-wine6-stable winecfg
```

## TIMQQ 标题框显示白框(操作未解决问题)
字体可能需要从win下载再试试
```
# 下载字体
git clone git@github.com:L-King-H/msyh.ttc.git
cd msyh.ttc
cp 微软雅黑/* ~/.deepinwine/Spark-TIM/drive_c/windows/Fonts/
cd ~/.deepinwine/Spark-TIM/drive_c/windows/Fonts/ 
mv MSYH.TTC  msyh.ttc
```

```
# 创建一个reg文件
# filename: msyh_config.reg
REGEDIT4
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink]
"Lucida Sans Unicode"="msyh.ttc"
"Microsoft Sans Serif"="msyh.ttc"
"MS Sans Serif"="msyh.ttc"
"Tahoma"="msyh.ttc"
"Tahoma Bold"="msyhbd.ttc"
"msyh"="msyh.ttc"
"Arial"="msyh.ttc"
"Arial Black"="msyh.ttc"
```

```
# 注册表生效，这里会包一个错
cd ~/.deepinwine/Spark-TIM
env WINEPREFIX="$HOME/.deepinwine/Spark-TIM/" deepin-wine5 regedit msyh_config.reg
```
