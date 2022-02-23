# nc archlinux 配置
nc 是netcat的简称，在manjaro安装过程中发现有不同的版本，如gnu-netcat、nmap，为了和linux服务器对应安装nmap

## 安装
```
sudo pacman -S nmap
sudo ln -s /usr/bin/ncat /usr/bin/nc
```

## 传输文件
```
# server 
pv nvim.appimage| nc -l 4444

# client
nc 10.18.32.193 4444|pv > nvim.appimage.del
```

## 打包pv传输

```
# server
tar czf - * | pv | nc -l --send-only -p 4444

#client
nc --recv-only <server_ip> 4444 | pv | tar xfz - -C . 
```

## 打包传输
```
# server
tar czfv - Update-servers.md | nc --send-only  -l -p 4444

# client
nc --recv-only  10.18.32.193 4444 | tar xfzv - -C /tmp/
```
