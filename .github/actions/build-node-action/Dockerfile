FROM centos:6.6
LABEL maintainer="joe@rstudio.com"

# COPY CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo
RUN sed -e "s|^mirrorlist=|#mirrorlist=|g" -e "s|^#baseurl=http://mirror.centos.org/centos/\$releasever|baseurl=https://mirrors.aliyun.com/centos-vault/6.6|g" -i.bak /etc/yum.repos.d/CentOS-*.repo
RUN yum makecache

# RUN yum clean all
# RUN yum makecache
# RUN curl -o /etc/yum.repos.d/CentOS-Base.repo http://www.xmpan.com/Centos-6-Vault-Aliyun.repo
RUN yum -y install centos-release-SCL
RUN sed -e "s|^baseurl=http://mirror.centos.org/centos/\$releasever|baseurl=https://mirrors.aliyun.com/centos-vault/6.6|g" -i.bak /etc/yum.repos.d/CentOS-*.repo
COPY centos6-scl-eol.repo /etc/yum.repos.d/CentOS-SCLo-scl.repo 
COPY centos6-scl-rh-eol.repo /etc/yum.repos.d/CentOS-SCLo-scl-rh.repo
COPY RPM-GPG-KEY-CentOS-SIG-SCLo /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo
RUN yum makecache
RUN curl -o libquadmath-7.2.1-1.2.1.el6.x86_64.rpm http://cernet.mirrors.ustc.edu.cn/centos-vault/centos/6/os/x86_64/Packages/libquadmath-7.2.1-1.2.1.el6.x86_64.rpm
RUN curl -o libgfortran4-7.2.1-1.2.1.el6.x86_64.rpm http://cernet.mirrors.ustc.edu.cn/centos-vault/centos/6/os/x86_64/Packages/libgfortran4-7.2.1-1.2.1.el6.x86_64.rpm
RUN rpm -ivh libquadmath-7.2.1-1.2.1.el6.x86_64.rpm
RUN rpm -ivh libgfortran4-7.2.1-1.2.1.el6.x86_64.rpm
# RUN curl -o /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo https://www.centos.org/keys/RPM-GPG-KEY-CentOS-SIG-SCLo
# RUN curl https://www.getpagespeed.com/files/centos6-scl-eol.repo --output /etc/yum.repos.d/CentOS-SCLo-scl.repo 
# RUN curl https://www.getpagespeed.com/files/centos6-scl-rh-eol.repo --output /etc/yum.repos.d/CentOS-SCLo-scl-rh.repo
RUN yum -y install python27
RUN yum -y install gcc-gfortran
RUN yum -y install devtoolset-7
RUN yum -y install tar
RUN yum -y install git
RUN yum -y install xz

COPY make-node.sh /make-node.sh

ENTRYPOINT [ "/make-node.sh" ]
