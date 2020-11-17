#petalinux 2018.3 environment
FROM ubuntu:16.04
ENV DEBIAN_FRONTEND=noninteractive \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8


# add user
ARG UID=1000
RUN useradd -m -u ${UID} docker-user

#copy file
COPY petalinux-v2018.3-final-installer.run /home/docker-user/
COPY install.txt /root/
COPY design_1_wrapper.hdf /home/docker-user/
#RUN locale-gen

RUN chmod +x /home/docker-user/petalinux-v2018.3-final-installer.run
RUN apt-get update && apt-get upgrade -y 
RUN dpkg --add-architecture i386 && apt-get update
RUN /root/install.txt

RUN mkdir -p /opt/pkg/petalinux/2018.3/
RUN chown docker-user:docker-user /opt/pkg/petalinux/2018.3/


USER ${UID}
RUN bash
WORKDIR /home/docker-user
RUN (yes | /home/docker-user/petalinux-v2018.3-final-installer.run  /opt/pkg/petalinux/2018.3/ )

#build petalinux
#COPY design_1_wrapper.xsa /home/docker-user/
#RUN  mkdir -p /home/docker-user/petalinux
#WORKDIR /home/docker-user/petalinux
#RUN
