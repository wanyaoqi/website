---
sidebar_position: 5
---

# 自动缓存镜像到 ceph 存储

本文介绍如何配置自动缓存 glance 镜像到 ceph 存储。

当前镜像缓存到 ceph 存储的方式是先从 glance 下载到宿主机本地缓存，然后从宿主机缓存上传到 ceph 存储：
glance_storage->host_local_storage->ceph_storage

当开启自动缓存镜像到 ceph 存储时，在上传镜像到 glance时，glance 会自动缓存 glance 上的镜像到 ceph 存储：
glance_storage->ceph_storage


## 如何开启自动缓存镜像到 ceph 存储

```bash
# 更新存储开启自动缓存镜像到 ceph 存储
$ climc storage-update --auto-cache-images <ID>

# 创建 ceph 存储开启自动缓存镜像到 ceph 存储
$ climc storage-create --auto-cache-images ......
```

操作完后重启 glance 服务，`kubectl rollout restart deploy -n onecloud default-glance`
