# MacBook 安装 Manjaro
  2013年的老mac已经无法适应新系统的升级、电池鼓包以后考虑放家里作为一个临时机器使用。
  CPU: i5
  Mem: 8G
  Disk: 256G

[toc]

---


## 第一 Manjaro 安装

  官网下载最新镜像，dd制作启动U盘，启动后按步骤操作。
### 1. 下载镜像文件和checksum文件
  ```
  # 如果返回OK表明下载的镜像是正确的
  sha1sum -c manjaro.iso.sha1

  ```

### 2. 找到USB
  ```
  ls -l /dev/disk/by-id | grep usb
  # […] usb-Flash_USB_Disk_xxxxxxxx-0:0 -> …/…/XdA
  ```

### 3. dd镜像到USB
  确认号自己的设备
  ```
  sudo dd if=manjaro.iso of=/dev/XdA bs=1M oflag=sync status=progress

  # dd结束以后对比镜像和USB设备是否一致
  sha1sum manjaro.iso
  sudo dd if=/dev/XdA iflag=count_bytes count=xxx | sha1sum
  ```

  问题：无法连接网络
  解答：USB连接你的安卓手机（苹果应该也有），选择“设置”，“连接与共享”，“USB共享网络”

## 02 - 配置macbook网卡
## 03 - i3wm + 配置推荐
## 04 - i3wm yay安装推荐软件
## 05 - 改键 xmodmap
## 06 - Alacritty + 字体配置推荐
## 07 - tmux配置+ 快捷键配置推荐
## 08 - 4K外接显示器配置xrandr
## 09 - WeChat+Linuxqq 适配4K显示器
    8G内存确实无法适应现在的需要，所以基本无法安装虚机器
## 10 - nvim+spacevim+coc.nvim
## 11 - 传输文件的利器nc
