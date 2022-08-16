
#docker build
docker build -t image_name .

#docker 起動方法
sudo docker run -d -P -v /home/y/work:/home/user/work -v /tmp/.X11-unix:/tmp/.X11-unix  -p 2022:22 --name docker_name image_name
ssh user@127.0.0.1 -p 2022



sudo docker run -d -P -v /home/y/work:/home/user/work --name peta20221 aa

#docker image作成方法
docker commit container_id image_name


#docker image更新
docker commit container_id repositoty:tag


