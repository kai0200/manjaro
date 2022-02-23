# pacman backup and recover

## 首先生成软件包列表

```
pacman -Qqen > packages-repository.txt
pacman -Qqem > packages-AUR.txt
```

## 重新安装：

```
pacman --needed -S - < packages-repository.txt
cat packages-AUR.txt | xargs yaourt -S --needed --noconfirm
```

## 清理多余软件包

```
yaourt -R `pacman -Qdqt`
```
