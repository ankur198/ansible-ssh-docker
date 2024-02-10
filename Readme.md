# Docker Ansible SSH

This is a simple example of how to use Docker to create a container with Ansible and SSH installed. This is useful for testing Ansible playbooks and roles.

# How to use

## Clone this repository

Since this repo contains files permission that are for root user, it is recommended to clone this repo as root user.

```bash
sudo su
git clone https://github.com/ankur198/ansible-ssh-docker
cd ansible-ssh-docker
```
Once cloned change permission of ssh files so that they are recognised as valid by running the following command: 
```bash
chmod 700 ./ssh && chmod 700 ./ssh/*
```

Make sure that file permissions are correct.
```bash
ls -la
```

It should look like this:

    total 32
    drwxr-xr-x  4 ankur ankur 4096 Feb 11 00:09 .
    drwxr-xr-x 46 ankur ankur 4096 Feb 10 22:29 ..
    -rw-r--r--  1 ankur ankur  440 Feb 11 00:14 docker-compose.yml
    -rw-r--r--  1 ankur ankur  189 Feb 11 00:10 Dockerfile.node
    -rw-r--r--  1 ankur ankur  128 Feb 10 22:38 Dockerfile.server
    drwxr-xr-x  8 ankur ankur 4096 Feb 11 00:18 .git
    drwx------  2 root  root  4096 Feb 11 00:17 ssh
    -rw-r--r--  1 ankur ankur 3312 Feb 10 23:46 sshd_config

and `ls -la ./ssh` should look like this:

    total 28
    drwx------ 2 root root 4096 Feb 11 00:39 .
    drwxr-xr-x 4 root root 4096 Feb 11 00:37 ..
    -rwx------ 1 root root 1142 Feb 11 00:37 authorized_keys
    -rwx------ 1 root root   36 Feb 11 00:37 config
    -rwx------ 1 root root 2602 Feb 11 00:37 id_rsa
    -rwx------ 1 root root  571 Feb 11 00:37 id_rsa.pub
    -rw-r--r-- 1 root root  142 Feb 11 00:39 known_hosts

## Start containers

```bash
docker compose up -d
```

## Exec into ansible-server

```bash
docker exec -it ansible-server bash
```

## Test SSH connection

From within shell of ansible-server execute the following

```bash
ssh root@ansible-client-1
```
