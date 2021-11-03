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
2. ```scp lustre@oss:~/packages/*.* ./packages```

Main packages are : 
wget https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kernel-3.10.0-1160.25.1.el7_lustre.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kmod-lustre-osd-ldiskfs-2.12.7-1.el7.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kernel-debuginfo-3.10.0-1160.25.1.el7_lustre.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-2.12.7-1.el7.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kernel-devel-3.10.0-1160.25.1.el7_lustre.x86_64.rpm  https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-ldiskfs-dkms-2.12.7-1.el7.noarch.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/kmod-lustre-2.12.7-1.el7.x86_64.rpm https://downloads.whamcloud.com/public/lustre/latest-release/el7/server/RPMS/x86_64/lustre-osd-ldiskfs-mount-2.12.7-1.el7.x86_64.rpm

After downloading try : ``` yum install *.rpm -y ``` 
Finishing installation : mkfs.lustre should work out. 

Check installed packages by : ```  rpm -qa | grep lustre ```

On my case installed packages were : 
```
kernel-devel-3.10.0-1160.25.1.el7_lustre.x86_64
kernel-3.10.0-1160.25.1.el7_lustre.x86_64
kmod-lustre-2.12.7-1.el7.x86_64
kmod-lustre-osd-ldiskfs-2.12.7-1.el7.x86_64
lustre-osd-ldiskfs-mount-2.12.7-1.el7.x86_64
lustre-ldiskfs-dkms-2.12.7-1.el7.noarch
kernel-debuginfo-3.10.0-1160.25.1.el7_lustre.x86_64
kernel-debuginfo-common-x86_64-3.10.0-1160.25.1.el7_lustre.x86_64
lustre-2.12.7-1.el7.x86_64
```

Configure lnet by editing :  ```vi /etc/modprobe.d/lnet.conf ```
On my case content was : ``` options lnet networks=tcp0(enp9s4f0) ``` , you may write ```eth0``` in the brackets. 

Format your secondary storage using : 
``` mkfs.lustre --fsname=lustre --mgs --mdt /dev/sda4 ``` 
Then mount : ``` mount -t lustre /dev/sda4 /mnt/MDS ``` 
by typing : mount 
Check if : 
``` /dev/sda4                       94G  5.5M   86G   1% /mnt/MDS ```

Create a modeprobe configuration file for the LNet ```/etc/modprobe.d/lnet.conf ``` and set the networks parameter as tcp0(eth0). Basically, you just need this one line on the file:  ``` options lnet networks=tcp0(eth0) ```

Check if the network is up by : ``` lctl network up```  
It should give ```lnet configured ``` message 

By executing : ``` lctl list_nids ``` we should get ``` 10.10.1.1@tcp ```

On OST site, format by ``` mkfs.lustre --ost --fsname=lustre --reformat --index=1 --mgsnode=10.10.1.1@tcp /dev/sda4 ```
and mount by : ```  mount -t lustre /dev/sda4 /mnt/ost0``` 

On ``` df -h ``` command you should get ``` /dev/sda4                      113G  1.3M  107G   1% /mnt/ost0 ```

On client site : Install client package only. 
```
yum -y install e2fsprogs \
    lustre-client \
    kernel-3.10.0-514.21.1.el7_lustre.x86_64 \
    kernel-devel-3.10.0-514.21.1.el7_lustre.x86_64 \
    kernel-headers-3.10.0-514.21.1.el7_lustre.x86_64
```
Install lustre modele and lnet.
Then mount : ``` mount -t lustre 10.10.1.1@tcp:/lustre /mnt ``` 
Check if mount worked out by executing ``` df -h ``` 
You should get ``` 10.10.1.1@tcp:/lustre          119G  3.7M  112G   1% /mnt ``` line if it worked out. 

You can try to copy zeros by executing : ``` dd if=/dev/zero of=/lustre bs=1k count=100k ```

The execution result is : 
``` 
102400+0 records in
102400+0 records out
104857600 bytes (105 MB) copied, 1.38912 s, 75.5 MB/s
```
