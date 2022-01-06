# nc

```
yay -S gnu-netcat

# 传输文件
nc -l 8888 > 1.tgz
nc [ip] 8888 < file.tgz

# 打包传输
nc -l 8888 | tar xfzv - 
tar czfv - * | nc ip 8888

```
