# find 命令

> TIME : 2024-07-22
> TAGS : Linux ; find

find [路径] [匹配条件] [动作]

## -name "xxx"

## -perm -u=xxx

- r : 可读
- w : 可写
- x : 可执行
- s : setuid:当文件被执行时, 用户将获得文件所有者的权限。
- S : setgid:当文件被执行时, 进程将继承文件的组 ID。
- t : sticky bit,:仅适用于目录, 表示只有文件所有者才能删除或重命名其拥有的文件。

## -type xxx

## 2>/dev/null

## find / -name "\*flag\*"

- find /: 从根目录（/）开始搜索整个文件系统
- -name "\*flag\*": 仅查找名称包含 "flag" 的文件和目录。星号（\*）表示通配符, 匹配任意长度的字符序列

## find / -perm -u=s -type f 2>/dev/null

find / -name "php.ini" -type f 2>/dev/null
cat /usr/local/php/etc/php.ini|grep

- -perm -u=s: 仅查找具有 setuid 位设置的文件。-perm 表示根据权限位筛选, -u=s 表示筛选具有 setuid 位的文件
- -type f: 仅查找普通文件, 不包括目录、硬链接等其他类型
- 2>/dev/null: 将错误消息重定向到/dev/null, 即忽略因权限不足而产生的错误消息

## find / -writable -type f 2>/dev/null

## find / -type f 2>/dev/null

## find / -type f -name "flag.txt" 2>/dev/null
