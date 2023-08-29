![image](./logo/logo-horizontal.png)

## ETCD Keeper Changes History

### 2023-Aug-29

Update the source code to setup permissions when user has permission to access all keys.

---

### 2023-Aug-28

Modify the Dockerfile to update the `ENTRYPOINT` from `shell form` to `exec form` in order we can pass the command arguments when launch docker container.

---

### Original Version

The original version of source code is fork from [evildecay/etcdkeeper](https://github.com/evildecay/etcdkeeper/tree/master) at commit of [58f8d84be2d6a8005475aad68ad1f4c7d85f218d](https://github.com/evildecay/etcdkeeper/commit/58f8d84be2d6a8005475aad68ad1f4c7d85f218d).
