FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive
RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
        tofrodos \
        iproute2 \
        gawk \
        net-tools \
        libncurses5-dev \
        libncursesw5-dev \
        zlib1g:i386 \
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
        screen \
        pax \
        gzip \
        python2.7 \
        binutils \
        cpio \
        expect \
        file \
        fonts-noto-cjk \
        git \
        git-lfs \
        gosu \
        lib32z1-dev \
        libglib2.0-dev \
        libgtk2.0-0 \
        libsdl1.2-dev \
        libtool-bin \
        locales \
        lsb-release \
        ncurses-dev \
        sudo \
        u-boot-tools \
        vim \
        xvfb \
        bc \
        rsync \
	libncurses5 \
	x11-apps \
	iputils-ping \
	net-tools \
	openssh-server \
	csh \
	libswt-gtk-4-jni \
	dbus-x11 \
	global \
	libtinfo-dev

ARG TZ=Asia/Tokyo
ARG USERNAME=user
ARG GROUPNAME=user
ARG UID=1000
ARG GID=1000
ARG PASSWORD=user
RUN groupadd -g $GID $GROUPNAME && \
    useradd -m -s /bin/bash -u $UID -g $GID -G sudo $USERNAME && \
    echo $USERNAME:$PASSWORD | chpasswd && \
    echo "$USERNAME   ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

	
RUN mkdir /var/run/sshd
RUN echo 'root:s' | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN mkdir -p /opt/pkg/petalinux/2022.1/
RUN mkdir -p /opt/pkg/petalinux/2021.2/
RUN mkdir -p /opt/pkg/petalinux/2021.1/
RUN mkdir -p /opt/pkg/petalinux/2020.3/
RUN mkdir -p /opt/pkg/petalinux/2020.2/
RUN mkdir -p /opt/pkg/petalinux/2020.1/
RUN mkdir -p /opt/pkg/petalinux/2018.3/
RUN chown user:user /opt/pkg/petalinux/2022.1/
RUN chown user:user /opt/pkg/petalinux/2021.2/
RUN chown user:user /opt/pkg/petalinux/2021.1/
RUN chown user:user /opt/pkg/petalinux/2020.3/
RUN chown user:user /opt/pkg/petalinux/2020.2/
RUN chown user:user /opt/pkg/petalinux/2020.1/
RUN chown user:user /opt/pkg/petalinux/2018.3/
RUN mkdir -p /home/user/work
RUN chown user:user /home/user/work
RUN mkdir -p /tools/Xilinx/
RUN chown user:user /tools/Xilinx

RUN locale-gen en_US.UTF-8 && \
    update-locale

ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8


# SSH login fix. Otherwise user is kicked off after login
#RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile
RUN echo "export DISPLAY=:0" >> /home/user/.bashrc

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
