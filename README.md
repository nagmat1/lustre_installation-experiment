Lustre file system installation : 
#```vi /etc/hosts```

```
127.0.0.1   localhost localhost.localdomain

10.52.3.196 mgs
10.52.3.101 oss1
10.52.3.102 oss2
```

Then, execute : 
```
yum -y install epel-release
rpm -ivh http://download.zfsonlinux.org/epel/zfs-release.el7.centos.noarch.rpm
yum -y install chrony
systemctl start chronyd
systemctl enable chronyd
```
edit ```vi /etc/yum.repos.d/lustre.repo ``` 
```
[lustre-server]
name=lustre-server
baseurl=https://downloads.whamcloud.com/public/lustre/latest-release/el7/server
# exclude=*debuginfo*
gpgcheck=0

[lustre-client]
name=lustre-client
baseurl=https://downloads.whamcloud.com/public/lustre/latest-release/el7/client
# exclude=*debuginfo*
gpgcheck=0

[e2fsprogs-wc]
name=e2fsprogs-wc
baseurl=https://downloads.whamcloud.com/public/e2fsprogs/latest/el7
# exclude=*debuginfo*
gpgcheck=0
```


Copy the needed packages from 
1. ```https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/ ``` 
or copy them from other servers:
2. ``` sudo scp lustre@oss:~/packages/*.* ./packages```

on /etc/yum.repos.d/lustre.repo edit: 
```
[lustre-server]
name=lustre-server
baseurl=https://downloads.whamcloud.com/public/lustre/latest-release/el7/server
# exclude=*debuginfo*
gpgcheck=0

[lustre-client]
name=lustre-client
baseurl=https://downloads.whamcloud.com/public/lustre/latest-release/el7/client
# exclude=*debuginfo*
gpgcheck=0

[e2fsprogs-wc]
name=e2fsprogs-wc
baseurl=https://downloads.whamcloud.com/public/e2fsprogs/latest/el7
# exclude=*debuginfo*
gpgcheck=0
```
