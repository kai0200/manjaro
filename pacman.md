# pacman

## 覆盖升级
rsync 同步系统文件、通过启动U盘重新覆盖安装系统后，pacman报错“exists in filesystem pacman”，不能直接删除以上文件，程序可能会报错，选择覆盖升级。
```
pacman --overwrite "*" -Syu
```

<++>

## 查看软件包含什么文件
查看软件包所在目录
```
sudo pacman -Qil package_name
```

## 查找文件属于那个包
```
sudo pacman -Qo <filename>
```

