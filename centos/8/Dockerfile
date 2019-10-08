FROM centos:8
MAINTAINER Roman Tsisyk <roman@tarantool.org>

# Fix missing locales
ENV LANGUAGE="en_US.UTF-8"

# Enable extra repositories
RUN yum -y install \
    wget \
    yum-utils \
    epel-release
RUN curl -s https://packagecloud.io/install/repositories/packpack/backports/script.rpm.sh | bash

# Install base toolset
RUN yum -y groupinstall 'Development Tools'
RUN yum -y install \
    cmake \
    sudo

# Install python2 for testing
RUN dnf -y install python2
RUN pip2 install gevent

# Enable sudo without tty
RUN sed -i.bak -n -e '/^Defaults.*requiretty/ { s/^/# /;};/^%wheel.*ALL$/ { s/^/# / ;} ;/^#.*wheel.*NOPASSWD/ { s/^#[ ]*//;};p' /etc/sudoers
