#    //  什么是 youshandefeiyang/allinone ?

allinone 是斗鱼，虎牙，抖音等直播平台的直播源代理程序，可以直接观看多个流畅完美满血 4K 源。除了 Docker 外，还提供了主流平台的二进制文件，包括 exe 格式。

#   //   Docker/DockerHub 国内镜像源/加速列表[整理分享](https://www.xuxlc.cn/article/details-40.html)


##  //例：docker镜像加速域名(docker.1ms.run/)


#  //    Docker安装allinone


docker run -d \
   --restart unless-stopped \
   --name allinone \
   --net=host \
   --privileged=true \
   -p 35455:35455 \
   docker.1ms.run/youshandefeiyang/allinone
   
   


#  //	进阶1:配置 watchtower 每天早上五点自动监听 allinone 镜像更新

  
docker run -d \
   --name watchtower \
   --restart unless-stopped \
   -v /var/run/docker.sock:/var/run/docker.sock \
   docker.1ms.run/containrrr/watchtower \
   allinone -c --schedule "0 0 5 * * *"



#  //	进阶2：直播源分组


docker run -d \
   --restart=always \
   --name allinone_format \
   -p 35456:35456 \
   docker.1ms.run/yuexuangu/allinone_format:latest




##	格式：http://【群晖IP】:35456/tv.php?h=【allinoneIP】&p=【allinonePort】&m=1&t=0

##	例：http://192.168.0.5:35456/tv.php?h=192.168.0.5&p=35455&m=1&t=0

##	例：http://192.168.0.5:35456/tv.php?h=192.168.0.5&p=35455&m=1&t=1











