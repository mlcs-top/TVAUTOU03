









#  //	Docker直播源项目


#  //	docker.1ms.run/（docker镜像加速域名）


##	Docker安装allinone
# 运行容器
docker run -d \
   --restart unless-stopped \
   --name allinone \
   --net=host \
   --privileged=true \
   -p 35455:35455 \
   docker.1ms.run/youshandefeiyang/allinone


#  //	进阶1

##   配置 watchtower 每天早上五点自动监听 allinone 镜像更新
docker run -d \
   --name watchtower \
   --restart unless-stopped \
   -v /var/run/docker.sock:/var/run/docker.sock \
   docker.1ms.run/containrrr/watchtower \
   allinone -c --schedule "0 0 5 * * *"



#  //	进阶2

## 运行容器
docker run -d \
   --restart=always \
   --name allinone_format \
   -p 35456:35456 \
   docker.1ms.run/yuexuangu/allinone_format:latest




##	格式：http://【群晖IP】:35456/tv.php?h=【allinoneIP】&p=【allinonePort】&m=1&t=0

##	例：http://192.168.0.5:35456/tv.php?h=192.168.0.5&p=35455&m=1&t=0

##	例：http://192.168.0.5:35456/tv.php?h=192.168.0.5&p=35455&m=1&t=1











