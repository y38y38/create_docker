#petalinux 2020.1 environment
FROM ubuntu:18.04

# add user
ARG UID=1000
RUN useradd -m -u ${UID} docker-user

#copy file
COPY petalinux-v2020.1-final-installer.run /home/docker-user/
COPY install.txt /root/
COPY design_1_wrapper.xsa /home/docker-user/

RUN chmod +x /home/docker-user/petalinux-v2020.1-final-installer.run
RUN apt-get update && apt-get upgrade -y 
RUN dpkg --add-architecture i386 && apt-get update
RUN /root/install.txt

RUN mkdir -p /opt/pkg/petalinux/2020.1/
RUN chown docker-user:docker-user /opt/pkg/petalinux/2020.1/


USER ${UID}
RUN bash
WORKDIR /home/docker-user
RUN (yes | /home/docker-user/petalinux-v2020.1-final-installer.run --dir /opt/pkg/petalinux/2020.1/ )

