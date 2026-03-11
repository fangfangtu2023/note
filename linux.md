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

### 方法二：rsync

适合重复同步，速度更稳，也方便增量传输。

```bash
rsync -avz ./dist/ root@1.2.3.4:/data/www/dist/
```

### 常见前提

- 本地能连上远程服务器
- 服务器已开启 SSH
- 目标目录有写入权限

### 常见报错方向

- `Permission denied`：权限不对，或者 SSH key / 账号不对
- `No such file or directory`：远程目录不存在
- `Connection refused`：服务器 SSH 没开，或者端口不对

### 补充

如果服务器 SSH 端口不是默认的 `22`：

```bash
scp -P 端口号 /本地文件路径 username@服务器IP:/远程目录/
rsync -avz -e "ssh -p 端口号" ./dist/ username@服务器IP:/远程目录/
```
