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

Install the latest Lustre-enabled kernel and the Lustre client on all nodes: 
```
yum -y install e2fsprogs \
    lustre-client \
    kernel-3.10.0-514.21.1.el7_lustre.x86_64 \
    kernel-devel-3.10.0-514.21.1.el7_lustre.x86_64 \
    kernel-headers-3.10.0-514.21.1.el7_lustre.x86_64
```

Copy the needed packages from 
1. ```https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/ ``` 
or copy them from other servers:
2. ``` sudo scp lustre@oss:~/packages/*.* ./packages```

To check installed packages : 
```
rpm -qa | grep lustre
```

Main packages are : 
1. wget https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-ldiskfs-dkms-2.12.7-1.el7.noarch.rpm
2. wget https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-osd-ldiskfs-mount-2.12.7-1.el7.x86_64.rpm
3. wget https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kmod-lustre-2.12.7-1.el7.x86_64.rpm
