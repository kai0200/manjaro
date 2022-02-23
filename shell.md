# shell 命令总结

## 常用命令

| command         | description |
|-----------------|-------------|
| readlink -f     |             |
| basename        |             |
| bashtop         |             |
| pv              |             |
| shutdown -h now |             |

### chmod 
```
chmod g-rw haha.dat ## 表示将haha.dat对所属组的rw权限取消
chmod o-rw haha.dat ## 表示将haha.dat对其他人的rw权限取消
chmod u+x haha.dat  ## 表示将haha.dat对所属用户的权限增加x
chmod a-x haha.dat  ## 表示将haha.dat对所用户取消x权限
```

### chown
```
<只有root权限能执行>
chown angela  aaa        ## 改变所属用户
chown :angela  aaa        ## 改变所属组
chown angela:angela aaa/    ## 同时修改所属用户和所属组
```
