# sogou输入法

先运行sudo pacman -Sy base-devel ，之后再执行yaourt fcitx-sogoupinyin，按照后续提示安装即可（构建PKGBUILD时直接忽略）

安装完成后输入命令sudo nano ~/.xprofile

添加： 
  export GTK_IM_MODULE=fcitx
  export QT_IM_MODULE=fcitx
  export XMODIFIERS="@im=fcitx"。

sogou输入法，在升级内核以后应该尝试重新编译安装。


