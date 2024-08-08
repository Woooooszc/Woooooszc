# Python 开启简单 web 服务

> Time : 2024-07-30
> TAGS : Python ; WEB

使用 Python 的内置 HTTP 服务器模块来快速启动一个简单的 Web 服务，从而让其他主机能够访问指定目录

## python2

```bash
python -m SimpleHTTPServer [port_number]
```

## python3

```bash
python3 -m http.server [port_number]
```

## 其他主机访问

`http://your_ip_address:[port_number]/`
