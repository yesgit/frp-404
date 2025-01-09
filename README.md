# frp

[![frps](http://dockeri.co/image/hedw/frps)](https://hub.docker.com/r/hedw/frps)
[![frpc](http://dockeri.co/image/hedw/frpc)](https://hub.docker.com/r/hedw/frpc)

Docker Images for Frp Based on Alpine and Debian.

 (amd64, arm32v5, arm32v6, arm32v7, arm64v8, i386, mips64le, ppc64le,riscv64, s390x)
 
### [Documentation](https://gofrp.org/en/)
### [中文文档](https://gofrp.org/zh-cn/docs/)

## Usage

### Basic

```bash
docker run --restart=always --network host -d -v /etc/frp/frps.toml:/etc/frp/frps.toml --name frps hedw/frps
docker run --restart=always --network host -d -v /etc/frp/frpc.toml:/etc/frp/frpc.toml --name frpc hedw/frpc
```

### Alpine

```bash
docker run --restart=always --network host -d -v /etc/frp/frps.toml:/etc/frp/frps.toml --name frps hedw/frps:alpine
docker run --restart=always --network host -d -v /etc/frp/frpc.toml:/etc/frp/frpc.toml --name frpc hedw/frpc:alpine
```

### Debian

```bash
docker run --restart=always --network host -d -v /etc/frp/frps.toml:/etc/frp/frps.toml --name frps hedw/frps:debian
docker run --restart=always --network host -d -v /etc/frp/frpc.toml:/etc/frp/frpc.toml --name frpc hedw/frpc:debian
```

```bash
docker run --restart=always --network host -d -v /etc/frp/frps.toml:/etc/frp/frps.toml --name frps hedw/frps:bookworm
docker run --restart=always --network host -d -v /etc/frp/frpc.toml:/etc/frp/frpc.toml --name frpc hedw/frpc:bookworm
```
