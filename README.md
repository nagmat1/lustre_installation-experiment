Build and Install Lustre from Source Code 

```
sed -i '/^SELINUX=/s/.*/SELINUX=disabled/' /etc/selinux/config
yum groupinstall "Development tools"
yum -y install epel-release

yum -y install xmlto asciidoc elfutils-libelf-devel zlib-devel \
       libyaml-devel kernel-devel binutils-devel newt-devel \
       python-devel hmaccalc perl-ExtUtils-Embed bison \
       elfutils-devel audit-libs-devel python-docutils \
       sg3_utils expect attr lsof quilt libselinux-devel \
       e2fsprogs e2fsprogs-devel
yum -y install --enablerepo=base-debuginfo kernel-debuginfo kernel-debuginfo-common

git clone git://git.whamcloud.com/fs/lustre-release.git
cd lustre-release
chmod 777 autogen.sh 
sh ./autogen.sh
yum install libnl3-devel
./configure --with-linux=/usr/src/kernels/$(uname -r)
make rpms
yum -y install *.$(arch).rpm
reboot
```

After rebooting try the next steps : 

```

```
