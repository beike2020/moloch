FROM centos:8
MAINTAINER Andy Wick <andy.wick@oath.com>

RUN \
yum -y update; \
yum -y install scl-utils wget; \
yum -y update; \
yum -y install git sudo perl-Test perl-Test-Simple bzip2 wget ruby-devel rubygems rpm-build pango which make; \
(cd /etc/yum.repos.d/; wget https://packages.ntop.org/centos/ntop.repo); \
rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm; \
rpm -ivh http://rpms.remirepo.net/enterprise/remi-release-8.rpm; \
yum -y install dnf-plugins-core; \
dnf config-manager --set-enabled PowerTools; \
dnf config-manager --set-enabled remi; \
yum -y clean all; \
yum -y update; \
yum -y install gcc gcc-c++ pfring python2 python3-pip perl-Test-Harness; \
git clone https://github.com/aol/moloch; \
(cd moloch ; ./easybutton-build.sh --daq --pfring); \
mv moloch/thirdparty /; \
rm -rf moloch; \
gem install --no-ri --no-rdoc fpm; \
pip3 install awscli; \
useradd -u 2000 elasticsearch; \
yum -y clean all; \
rm -rf /var/cache/yum
