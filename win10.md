# win10配置过程

## 修改键盘布局
```
https://github.com/microsoft/PowerToys
下载安装按图形界面配置
```

## wsl2 Manjaro 安装yay
```
pacman -S --needed git base-devel

git clone https://aur.archlinux.org/yay.git

cd yay

makepkg -si
# 安装慢go设置代理
go env -w GOPROXY=https://goproxy.cn,direct
export GOPROXY=https://mirrors.aliyun.com/goproxy/

# 一条命令处理
pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si

# 第一次使用
yay -Syu --devel
yay -Y --devel --save
```

## copy /usr/bin/tty-clock
```
cp tty-clock ~/bin/tty-clock /usr/bin/

echo 'alias clock 'tty-clock -tbscf %Y-%m-%d'  >> ~/.config/fish/config.fish
```
