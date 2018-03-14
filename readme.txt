本镜像的特点
已设置时区为：Asia/Shanghai。
解决了某些云服务器上Tomcat启动过慢问题（随机数产生器初始化过慢）。

如何使用本镜像
测试启动Tomcat:
$ docker run -it --rm -p 80:8080 jianuo/docker-tomcat:latest
可以通过浏览器访问 http://localhost 或 http://host-ip来测试Tomcat是否启动成功。

部署应用，启动Tomcat:
例如：将/home/app，部署成根路径项目，并将Tomcat和app的日志，均输出到/data/appLogs目录。

$ docker run -d --name tomcat-app -p 80:8080 \ 
	-v /data/app:/usr/local/tomcat/webapps/ROOT \ 
	-v /data/Logs:/usr/local/tomcat/logs \ 
	jianuo/docker-tomcat:latest
注意：app的日志文件输出路径须为相对路径：logs（对应的绝对路径为：{$CATALINA_HOME}/logs）。

Tomcat环境相关:
CATALINA_HOME:   /usr/local/tomcat
JRE_HOME:        /usr
