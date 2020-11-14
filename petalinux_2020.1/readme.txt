1)get petalinux install file
example petalinux-v2020.1-final-installer.run

2)build
docker build -t image-name:version Dockerfile-directory

example 
#docker build build -t pl:1 .

3)
docker run -it --name containername image-name:version

example 
#docker run -it --name pl-8 pl:1


