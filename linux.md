# Linux

## mac 如何将本地文件推送到远程服务器指定文件夹里面去

最常用的方法是 `scp` 或 `rsync`。

### 方法一：scp

```bash
scp /本地文件路径 username@服务器IP:/远程目录/
```

示例：

```bash
scp ./test.txt root@1.2.3.4:/data/www/
```

如果要传整个文件夹：

```bash
scp -r ./dist root@1.2.3.4:/data/www/
```

