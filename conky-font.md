# 安装manjaro-i3 版本conky乱码

## 现象
安装后发现屏幕右上方插件显示“年月日”乱码。

## 安装字体
```
sudo pacman -S wqy-bitmapfont
sudo pacman -S wqy-zenhei
```

## 修改文件
```
sudo vim /usr/share/conky/conky_maia
```

## 编辑日期相关字段更换字体
更换相关4行代码，删除原有复制粘贴即可。
```
conky.text = [[
{voffset 8}color2{font WenQuanYi Zenhei:size=16}{time %A }font\
{voffset -8}alignrcolor{font WenQuanYi Zenhei:size=38}{time %e}font
color{voffset -30}color{font WenQuanYi Zenhei:size=18}{time %b}font\
{voffset -3} color{font WenQuanYi Zenhei:size=20}{time %Y}$fontcolor2hr
....
```
## 修改好自动生效，conky进程会自动刷新
