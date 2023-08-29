![image](./logo/logo-horizontal.png)

## ETCD Keeper

This version is the fork branch from [evildecay/etcdkeeper](https://github.com/evildecay/etcdkeeper/tree/master) which modify the Dockerfile in order we can pass the argument to docker to setup the authentication and etc. For the changes history, please refer to [here](./CHANGES.md).

### Example

By using this version of docker image, we can pass the arguments to command. Otherwise, we need to override entirely entrypoint.


```yml
etcdkeeper-local-auth:
  image: ghcr.io/faganooi/etcdkeeper:20230829123835 #"evildecay/etcdkeeper"
  container_name: etcdkeeper-local-auth
  command: ["-auth=true"]
  # Below is the example of entrypoint we need to override if we use original version from evildecay/etcdkeeper.
  # entrypoint: ["./etcdkeeper.bin", "-h", "0.0.0.0", "-p", "8080", "-auth=true"]
  ports:
    - "9000:8080"
```

### Usage (Docker Command arguments)

```
  -sep string
        Separator (default "/")
  -usetls bool
        use tls (only v3)
  -cacert string
        verify certificates of TLS-enabled secure servers using this CA bundle (only v3)
  -cert string
        identify secure client using this TLS certificate file (only v3)
  -key string
        identify secure client using this TLS key file (only v3)
  -auth bool
        use etcd auth
  -timeout int
        ETCD client connect timeout
```

### Role and example

It is example to create role and user which grant permissions to read all keys.
Below command required to run inside docker container by running command of `docker exec -it <container name> bash`.

```
etcdctl role add read_only_role

etcdctl role grant-permission read_only_role --prefix=true read ''

etcdctl user add readUser:readUserPwd

etcdctl user grant-role readUser read_only_role
```
