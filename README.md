Docker Debian NSS Wrapper
=========================

**Forked from https://github.com/atbentley/docker-nss-wrapper**
**Modification: adding Debian support**

A Docker image that uses NSS Wrapper to modify /etc/passwd so arbitrary UIDs can run and still have a username.

This is most useful in environments such as Openshift which randomise the UID for each container.

Use the `$USER_NAME` environment variable to configure the name for the user.

``` dockerfile
FROM ylamothe/nss-wrapper:debian

ENV USER_NAME=ylamothe
```

``` bash
$ docker run -u 1111111111 my-image id -u
1111111111
$ docker run -u 1111111111 my-image whoami
atbentley
```

`$USER_NAME` defaults to root.

