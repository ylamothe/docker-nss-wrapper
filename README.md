Docker CentOS NSS Wrapper
=========================

A Docker image that uses NSS Wrapper to modify /etc/passwd so arbitrary UIDs can run and still have a username.

This is most useful in environments such as Openshift which randomise the UID for each container.

Use the `$USER_NAME` environment variable to configure the name for the user.

``` dockerfile
FROM atbentley/nss-wrapper:centos7

ENV USER_NAME=atbentley
```

``` bash
$ docker run -u 1111111111 my-image id -u
1111111111
$ docker run -u 1111111111 my-image whoami
atbentley
```

`$USER_NAME` defaults to root.

