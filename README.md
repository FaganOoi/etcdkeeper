![image](./logo/logo-horizontal.png)

## ETCD Keeper

This version is the fork branch from [evildecay/etcdkeeper](https://github.com/evildecay/etcdkeeper/tree/master) which modify the Dockerfile in order we can pass the argument to docker to setup the authentication and others flags used in source code.

### Example

By using this version of docker image, we can pass the arguments to command. Otherwise, we need to override entirely entrypoint.

\*\* `etcdkeeper-local` is the local docker image build from source code.

```yml
etcdkeeper-local-auth:
  image: etcdkeeper-local #"evildecay/etcdkeeper"
  container_name: etcdkeeper-local-auth
  command: ["-auth=true"]
  # Below is the example of entrypoint we need to override if we use original version from evildecay/etcdkeeper.
  # entrypoint: ["./etcdkeeper.bin", "-h", "0.0.0.0", "-p", "8080", "-auth=true"]
  ports:
    - "9000:8080"
```

### Usage (Docker Command arguments)

```
  -h string
        host name or ip address (default: "0.0.0.0", the http server addreess, not etcd address)
  -p int
        port (default 8080)
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
