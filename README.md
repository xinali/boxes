# boxes

主要是自己使用的一些docker镜像

## binbox 

研究二进制安全的docker，分别有x86/x64，两种版本，其中主要工具

```
gcc
gdb

radare2

pwntools
gef
peda
pwndbg
```

`docker`运行需要提升权限以用于`pwntools`的`gdb.attach`

```
docker -t -i --privileged docker_image
```

## mongodb

带有验证功能的mongodb docker