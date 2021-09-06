# lustre_installation
lustre file system installation tutorial

To start the installation, add these nodes on /etc/hosts of all nodes. The node names are all lower-case letters with no space, and the /etc/hosts looks like this:

127.0.0.1   localhost localhost.localdomain

172.31.47.35   client
172.31.44.215  mgs
172.31.44.227  mds
172.31.39.125  oss1
172.31.32.6    oss2
172.31.44.150  oss3

NOTE: You have to update /etc/hosts of all the nodes.

Next, install EPEL and ZFS repositories, and also install Chrony. (Chrony is a NTP implementation. You can also use ntp instead.):

yum -y install epel-release
rpm -ivh http://download.zfsonlinux.org/epel/zfs-release.el7.centos.noarch.rpm
yum -y install chrony
systemctl start chronyd
systemctl enable chronyd
NOTE: It is important to have the correct time on all nodes.

cat >/tmp/lustre-repo.conf <<\__EOF
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
__EOF

Install the latest Lustre-enabled kernel and the Lustre client on all nodes:

yum -y install e2fsprogs \
    lustre-client \
    kernel-3.10.0-514.21.1.el7_lustre.x86_64 \
    kernel-devel-3.10.0-514.21.1.el7_lustre.x86_64 \
    kernel-headers-3.10.0-514.21.1.el7_lustre.x86_64
Now you need to reboot all the nodes to boot the nodes with the Lustre-enabled kernel.


