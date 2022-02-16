# nc

```
yay -S gnu-netcat

# 传输文件
nc -l 8888 > 1.tgz
nc [ip] 8888 < file.tgz

# 打包传输
nc -l 8888 | tar xfzv - 
tar czfv - * | nc ip 8888

# nc -l -p 9999| tar xfzv - 


# server
tar czfv - Update-servers.md| nc --send-only  -l -p 4444

# client
nc --recv-only  10.18.32.193 4444|tar xfzv - -C /tmp/

# server 
pv nvim.appimage| nc -l 4444

# client
nc 10.18.32.193 4444|pv > nvim.appimage.del
```
