#petalinux 2018.2 environment
FROM ubuntu:16.04
ENV DEBIAN_FRONTEND=noninteractive \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8


# add user
ARG UID=1000
RUN useradd -m -u ${UID} docker-user

#copy file
COPY petalinux-v2018.2-final-installer.run /home/docker-user/
COPY design_1_wrapper.hdf /home/docker-user/
#RUN locale-gen

RUN chmod +x /home/docker-user/petalinux-v2018.2-final-installer.run
RUN apt-get update && apt-get upgrade -y 
RUN dpkg --add-architecture i386 && apt-get update
RUN apt-get -y install \ 
 apt-utils \
 tofrodos \
 gawk \
 xvfb \
 git \
 make \
 net-tools \
 libncurses5 \
 tftpd \
 zlib1g \
 libssl-dev \
 flex \
 bison \
 libselinux1 \
 gnupg \
 wget \
 diffstat \
 chrpath \
 socat \
 xterm \
 autoconf \
 libtool \
 tar \
 unzip \
 texinfo \
 zlib1g-dev \
 gcc-multilib \
 build-essential \
 libsdl1.2-dev \
 libncurses5-dev \
 libglib2.0-dev \
 screen \
 pax \
 gzip \
 zlib1g:i386 \
 cpio \
 rsync \
 locales \
 locales-all \
 sudo  \
 libc6-dev:i386 \
 libtool-bin \
 socat \
 python \
 xz-utils

RUN mkdir -p /opt/pkg/petalinux/2018.2/
RUN chown docker-user:docker-user /opt/pkg/petalinux/2018.2/


USER ${UID}
RUN bash
WORKDIR /home/docker-user
RUN (yes | /home/docker-user/petalinux-v2018.2-final-installer.run  /opt/pkg/petalinux/2018.2/ )

#build petalinux
#COPY design_1_wrapper.xsa /home/docker-user/
#RUN  mkdir -p /home/docker-user/petalinux
#WORKDIR /home/docker-user/petalinux
#RUN
