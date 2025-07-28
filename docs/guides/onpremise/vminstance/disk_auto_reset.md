---
sidebar_position: 14
---

# 关机自动重置磁盘

磁盘打开关机自动重置，虚机启动后磁盘写入到临时文件，不改变当前磁盘的数据，虚机关机时会自动删除临时文件。

## 如何打开磁盘关机自动重置

```bash
$ climc disk-update --auto-reset <DISK_ID>
```

虚机重启后生效。

## 配置临时文件目录

临时文件是默认写入到磁盘所在的文件夹，但是由于 lvm 是非文件存储，所以需要配置临时文件目录。

```bash
$ vi /etc/yunion/host.conf
reset_disk_tmp_dir: /opt/cloud/workspace/disks
```

重启 host-agent 服务后生效。