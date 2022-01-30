


# 使用阿里云NAS

## 创建目录并把文件上传至nfs中
```
# 安装nfs客户端工具
yum install -y nfs-utils

# 挂载
mount -t nfs -o vers=3,nolock,proto=tcp,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport **.cn-beijing.nas.aliyuncs.com:/ /mnt


# 解除挂载
cd ~ && umount /mnt
```

