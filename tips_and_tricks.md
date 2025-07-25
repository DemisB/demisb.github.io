# Tips & tricks

## Linux random stuff

- Create ssh key with 4096 something

`ssh-keygen -C "docker-build-read-only" -t rsa -b 4096`

- Create an ed25519 ssh key

`ssh-keygen -C "demis-github" -t ed25519`

- Repeating key MacOS (useful to know for IdeaVim)
https://stackoverflow.com/questions/39606031/intellij-key-repeating-idea-vim

- cmake
```bash
cmake -DBUILD_TESTS=ON -DBUILD_PYTHON_BINDINGS=OFF -DUSE_MULTITHREAD=OFF ..
cmake --build .
```

- linux package installed files
```bash
dpkg -L $package
```
cf https://serverfault.com/questions/96964/list-of-files-installed-from-apt-package

- find delete file with git
```bash
git log --diff-filter=D --summary
```
cf. https://stackoverflow.com/questions/6017987/how-can-i-list-all-the-deleted-files-in-a-git-repository

- String manipulation in bash (parameter expansion, etc.)

```bash
> smth="/path/to/something"
> echo ${smth##*/}
something

> echo $smth | sed "s/^.*\///gi"
something

> echo $smth | grep -oE "[^/]*$"
something
```

cf. https://mywiki.wooledge.org/BashFAQ/100, https://stackoverflow.com/questions/22727107/how-to-find-the-last-field-using-cut

- Clipboard

cf. https://stackoverflow.com/questions/749544/pipe-to-from-the-clipboard-in-a-bash-script#comment54347773_749544

- Boto3 tip

https://stackoverflow.com/questions/33549254/how-to-generate-url-from-boto3-in-amazon-web-services
https://github.com/boto/boto3/issues/110

- Update local routing table without pinging broadcast IP (deprecated)

```bash
nmap -sn 192.168.50.0/24
```

cf. https://superuser.com/questions/339863/why-doesnt-broadcast-ping-work#comment1155146_487014

SSL cert expiration https://www.howtouselinux.com/post/4-ways-to-check-ssl-certificate-expiration-date

- Format external drive (SD card, USB key)

```bash
sudo fdisk /dev/sdx
# Follow the instructions.
# Last time I chose to make a "W95 FAT32" partition type.
# Then, do (copy pasted from the command I used some time ago)
sudo mkfs.vfat -F32 -I /dev/sdx
```

- Create gzipped tar archive excluding node_modules and python venvs

```bash
tar --exclude=node_modules --exclude=".venv*" -czvf Dev.tgz ./Dev
```

## Database stuff

### MariaDB

**Run a command in a local container**

(e.g. to generate a password hash)

```bash
$ docker run -e MYSQL_ROOT_PASSWORD=mypass -p 3306:3306 -d mariadb:latest
$ docker exec -it competent_ardinghelli /bin/bash

# MariaDB shell:
MariaDB [(none)]> SELECT SHA2('mon super password', 256);
```

### Clickhouse

**Run a command in a local container**

(e.g. to generate a password hash)

```bash
$ docker run -d --name some-clickhouse-server --ulimit nofile=262144:262144 clickhouse/clickhouse-server
$ docker exec -it some-clickhouse-server clickhouse-client

# Clickhouse shell:
fef4225447e1 :) SELECT hex(SHA256('pwd'));
```

### Redis

```
# Show the number of dbs
CONFIG GET databases

# Example output:
# 1) "databases"
# 2) "16"

# Show dbs that have keys
INFO keyspace

# Example output:
# # Keyspace
# db3:keys=3,expires=0,avg_ttl=0
# db11:keys=2,expires=0,avg_ttl=0
# db15:keys=6,expires=0,avg_ttl=0

# Switch to a db
SELECT 15
```

