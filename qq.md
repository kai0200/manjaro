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
