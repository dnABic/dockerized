
### Build docker image which will run saltstack by systemd


Build it with:

```bash
docker build -f Dockerfile.systemd -t saltstack-systemd:v0.0.1 .
```

Start container:

```bash
docker run --name=saltsystemdtest \
      --cap-add=SYS_ADMIN \
      --detach \
      --volume /sys/fs/cgroup:/sys/fs/cgroup:ro \
      --tmpfs /run \
      --tmpfs /run/lock \
      saltstack-systemd:v0.0.1
```

Check that services are up:

```bash
docker exec -ti saltsystemdtest bash -c 'ps auxw'
```
