# 安装
```shell
$ chmod +x ./install.sh
$ sudo ./install.sh
```

# 配置管理员客户端
```shell
$ mc config host add minio http://{IP}:9000 minioadmin minioadmin
```

# 添加用户
```shell
$ mc admin user add minio miniouser1 miniopassword1
```

# 限定用户访问特写bucket

## 创建policy
```shell
$ sed 's/BUCKETNAME/{bucketname}/' policy.json > tmp.json
$ mc admin policy add minio {policyname} tmp.json
```

## 绑定用户
```shell
$ mc admin policy set minio {policyname} user=miniouser1
```

## 创建group批量绑定用户
```shell
$ mc admin group add minio group1 miniouser2 miniouser3
$ mc admin policy set minio {policyname} group=group11
```

# 更多信息
https://docs.min.io/docs/minio-admin-complete-guide.html
