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
wget https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kernel-3.10.0-1160.25.1.el7_lustre.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kmod-lustre-osd-ldiskfs-2.12.7-1.el7.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kernel-debuginfo-3.10.0-1160.25.1.el7_lustre.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-2.12.7-1.el7.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kernel-devel-3.10.0-1160.25.1.el7_lustre.x86_64.rpm  https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-ldiskfs-dkms-2.12.7-1.el7.noarch.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kmod-lustre-2.12.7-1.el7.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-osd-ldiskfs-mount-2.12.7-1.el7.x86_64.rpm

After downloading try : ``` yum install *.rpm ``` 
Finishing installation : mkfs.lustre should work out. 

Format your secondary storage using : 
``` sudo mkfs.lustre --fsname=lustre --mgs --mdt /dev/sda4 ``` 
Then mount : ``` mount -t lustre /dev/sda4 /mnt/MDS ``` 
by typing : mount 
Check if : 
``` /dev/sda4                       94G  5.5M   86G   1% /mnt/MDS ```

Create a modeprobe configuration file for the LNet ```/etc/modprobe.d/lnet.conf ``` and set the networks parameter as tcp0(eth0). Basically, you just need this one line on the file:  ``` options lnet networks=tcp0(eth0) ```

Check if the network is up by : ``` lctl network up```  
It should give ```lnet configured ``` message 
