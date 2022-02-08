𝑰'𝒎 𝒉𝒉𝒈, 𝑰 𝒂𝒎 𝒂 𝒈𝒓𝒂𝒅𝒖𝒂𝒕𝒆 𝒔𝒕𝒖𝒅𝒆𝒏𝒕 𝒇𝒓𝒐𝒎 𝑵𝒂𝒏𝒋𝒊𝒏𝒈, 𝑪𝒉𝒊𝒏𝒂.

- :school: 𝑺𝒉𝒄𝒐𝒐𝒍: 𝑯𝒐𝒉𝒂𝒊 𝑼𝒏𝒊𝒗𝒆𝒓𝒔𝒊𝒕𝒚 
- 🌱 𝑳𝒆𝒂𝒓𝒏𝒊𝒏𝒈: 𝑰’𝒎 𝒄𝒖𝒓𝒓𝒆𝒏𝒕𝒍𝒚 𝒍𝒆𝒂𝒓𝒏𝒊𝒏𝒈 𝒅𝒆𝒔𝒊𝒈𝒏 𝒑𝒂𝒕𝒕𝒆𝒓𝒏, 𝑳𝒆𝒆𝒕𝒄𝒐𝒅𝒆, 𝒅𝒊𝒔𝒕𝒓𝒊𝒃𝒖𝒕𝒆𝒅 𝒔𝒚𝒔𝒕𝒆𝒎, 𝒎𝒊𝒅𝒅𝒍𝒆𝒘𝒂𝒓𝒆 𝒂𝒏𝒅 𝒔𝒐 𝒐𝒏.
- :heartbeat: 𝑯𝒐𝒘 𝒕𝒐 𝒓𝒆𝒂𝒄𝒉 𝒎𝒆：[𝑽𝑿](https://github.com/21want28k/pictures/blob/master/3143332f70bca07d7a6d8aaa85632f8.jpg)
- :books: 𝑴𝒚 𝒃𝒍𝒐𝒈: 𝒉𝒕𝒕𝒑𝒔://𝒉𝒉𝒈𝒚𝒚𝒅𝒔.𝒃𝒍𝒐𝒈.𝒄𝒔𝒅𝒏.𝒏𝒆𝒕/ 
- :briefcase: 𝑷𝒓𝒐𝒇𝒆𝒔𝒔𝒊𝒐𝒏𝒂𝒍 𝒔𝒌𝒊𝒍𝒍𝒔：𝒎𝒚 𝒅𝒓𝒆𝒂𝒎
![<img   height="19px" src="https://img.shields.io/badge/java-grey.svg?&logo=java&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/spring-%236DB33F.svg?logo=spring&logoColor=green"/> <img
        height="19px" src="https://img.shields.io/badge/ubuntu-%23E95420.svg?&logo=ubuntu&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/docker-%232496ED.svg?&logo=docker&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/mysql-%234479A1.svg?&logo=mysql&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/git-%23F05032.svg?&logo=git&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/redis-%23DC382D.svg?&logo=redis&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/rabbitmq-%23FF6600.svg?logo=rabbitmq&logoColor=white"/>](https://img-blog.csdnimg.cn/2b1281caade2476d99f13878fc24e111.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_20,color_FFFFFF,t_70,g_se,x_16)

为什么要用英文写呢？为了去外企，为了摆脱自己对英语的恐惧，不是装B。
## 1-1：Nacos Cluster Architecture Nacos集群架构
![在这里插入图片描述](https://img-blog.csdnimg.cn/2a3d465facbb4d429ce8244dcb7c7b91.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_16,color_FFFFFF,t_70,g_se,x_16)

The picutre comes from [Nacos](https://nacos.io/zh-cn/docs/cluster-mode-quick-start.html). It shows the main nacos cluster arch. As I understand it, there maybe an Nginx server exist in front of docker nacos cluster. So, I try to deploy an nacos cluster by using docker-compose technology and an Nginx server. This article aims to record the process of deploying and the peoblems during completing it.

## 1-2: Environment
- Docker-compose v2.2.2 : Different docker-compose version don't seem to be a problem.
- Nacos: v2.0.3 the latest
- MySQL: v5.7
- Nginx: v1.18.0
## 1-3: Project Arch and Nacos Deploment in Docker
![在这里插入图片描述](https://img-blog.csdnimg.cn/c0201618387046bea311af0b6fb3a79e.png)
- nacos-hostname.env
	```bash
	#nacos dev env
	PREFER_HOST_MODE=hostname
	# docker实例别名，可以换成ip port must be 8848
	NACOS_SERVERS=nacos1:8848 nacos2:8848 nacos3:8848
	MYSQL_SERVICE_HOST=mysql
	# 指定保存数据的数据库名称
	MYSQL_SERVICE_DB_NAME=nacos_devtest
	# 访问mysql端口
	MYSQL_SERVICE_PORT=3306
	# 访问mysql的用户名
	MYSQL_SERVICE_USER=root
	# 访问mysql的密码
	MYSQL_SERVICE_PASSWORD=root
	```
- custom.properties
	```bash
	#spring.security.enabled=false
	#management.security=false
	#security.basic.enabled=false
	#nacos.security.ignore.urls=/**
	#management.metrics.export.elastic.host=http://localhost:9200
	# metrics for prometheus
	management.endpoints.web.exposure.include=*
	
	# metrics for elastic search
	#management.metrics.export.elastic.enabled=false
	#management.metrics.export.elastic.host=http://localhost:9200
	
	# metrics for influx
	#management.metrics.export.influx.enabled=false
	#management.metrics.export.influx.db=springboot
	#management.metrics.export.influx.uri=http://localhost:8086
	#management.metrics.export.influx.auto-create-db=true
	#management.metrics.export.influx.consistency=one
	#management.metrics.export.influx.compressed=true
	```
- docker-compose.yml
	```yml
	version: "3"
	services:
	  mysql:
	    container_name: mysql
	    # 最新的mysql8版本
	    image: mysql:5.7
	    environment:
	      # mysql root用户密码
	      MYSQL_ROOT_PASSWORD: root
	    command:
	      --default-authentication-plugin=mysql_native_password
	      --character-set-server=utf8mb4
	      --collation-server=utf8mb4_general_ci
	      --explicit_defaults_for_timestamp=true
	      --lower_case_table_names=1
	      --max_allowed_packet=128M;
	    volumes:
	      # mysql的数据文件
	      - ./mysql/data:/var/lib/mysql
	      # mysql配置文件
	      - ./mysql/config:/etc/mysql/conf.d
	    ports:
	      - "3306:3306"
	  nacos1:
	    hostname: nacos1
	    container_name: nacos1
	    image: nacos/nacos-server:latest
	    volumes:
	      # 需要添加mysql8的插件
	      #- ./nacos/plugins/mysql/:/home/nacos/plugins/mysql/
	      # 把日志文件映射出来
	      - ./nacos/cluster-logs/nacos1:/home/nacos/logs
	      # 把配置文件映射出来
	      - ./nacos/init.d/custom.properties:/home/nacos/init.d/custom.properties
	    
	    environment:                       # 设置环境变量,相当于docker run命令中的-e
	      - JVM_XMS=512m
	      - JVM_XMX=512m
	      - JVM_XMN=128m
	      #- MODE=standalone
	    ports:
	      - "8848:8848"
	      - "9555:9555"
	    env_file:
	        # 集群配置文件
	      - ./nacos/env/nacos-hostname.env
	    restart: always
	    depends_on:
	      - mysql
	  nacos2:
	    hostname: nacos2
	    image: nacos/nacos-server:latest
	    container_name: nacos2
	    volumes:
	      #- ./nacos/plugins/mysql/:/home/nacos/plugins/mysql/
	      - ./nacos/cluster-logs/nacos2:/home/nacos/logs
	      - ./nacos/init.d/custom.properties:/home/nacos/init.d/custom.properties
	    environment:                        # 设置环境变量,相当于docker run命令中的-e
	      - JVM_XMS=512m
	      - JVM_XMX=512m
	      - JVM_XMN=128m
	    ports:
	      - "8849:8848"
	    env_file:
	      - ./nacos/env/nacos-hostname.env
	    restart: always
	    depends_on:
	      - mysql
	  nacos3:
	    hostname: nacos3
	    image: nacos/nacos-server:latest
	    container_name: nacos3
	    volumes:
	      #- ./nacos/plugins/mysql/:/home/nacos/plugins/mysql/
	      - ./nacos/cluster-logs/nacos3:/home/nacos/logs
	      - ./nacos/init.d/custom.properties:/home/nacos/init.d/custom.properties
	    environment:                      # 设置环境变量,相当于docker run命令中的-e
	      - JVM_XMS=512m
	      - JVM_XMX=512m
	      - JVM_XMN=128m
	    ports:
	      - "8850:8848"
	    env_file:
	      - ./nacos/env/nacos-hostname.env
	    restart: always
	    depends_on:
	      - mysql
	```
- Remember!!! The sql file should be imported into db nacos_devtest. [sql file download](https://github.com/alibaba/nacos/blob/master/distribution/conf/nacos-mysql.sql)
![在这里插入图片描述](https://img-blog.csdnimg.cn/17a66f1130704e328b58cbf4d9cc2fa4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_20,color_FFFFFF,t_70,g_se,x_16)


The files above refer to [get source code from gitee](https://gitee.com/ysdxhsw/docker-compose-nacos-mysql) and offical [nacos group](https://github.com/nacos-group/nacos-docker).

Success: <font color = red>**All nodes status are up**.</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/03dcb32dc55f425ea87e3a7e367259e1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_20,color_FFFFFF,t_70,g_se,x_16)
Create a dataId in one node and you will get the same in another.

<font color = blue>**Notes:**</font>
- In most cases, we may add port mappings in docker services. e.x. `- port "8849:8848"` i.e. Expose the 8848 port inside the container to the outside 8849 port. However, we may omits one problem. Let me show you. Firstly, when the docker-compose.yml is finished and deployed by `docker-compose up` command. Docker engine will create an network called `${dir}_defalut` like this:
	```bash
	(base) ➜  docker-compose-nacos-mysql-master docker network list    
	NETWORK ID     NAME                            DRIVER    SCOPE
	72eddc5e38ac   bridge                          bridge    local
	7348f4641015   docker-nacos_default            bridge    local <-----
	```
	We can inspect this network:
	```xml
     "Containers": {
        "185a008b417d09201c8e8efdc5b4b68776f994d797c32d9fbd523327c80cff80": {
            "Name": "nacos2",
            "EndpointID": "be3a4eba47b6d5908682ece4a9465390385ec5a10ab8b5730d7eb8c2d436c309",
            "MacAddress": "02:42:ac:1b:00:05",
            "IPv4Address": "172.27.0.5/16",
            "IPv6Address": ""
        },
        "1f09159bc54c43a4fb86eb84e083ab35354e727d1c1bd0a4cab448298e4c2b71": {
            "Name": "nacos1",
            "EndpointID": "a61935035f6940ad624ac68cd49af76faa1461146130bf1c4349157eed53232f",
            "MacAddress": "02:42:ac:1b:00:06",
            "IPv4Address": "172.27.0.6/16",
            "IPv6Address": ""
        },
        "b11c0f47fafb15b7523be1c63d5d8f9134c2705dad128ba46630bbff48fe40d8": {
            "Name": "nacos3",
            "EndpointID": "59d1641bff3f8250bb0c3e13e78c5e44e3c3caeaf8ed48ca7d72b6df6fd32f5b",
            "MacAddress": "02:42:ac:1b:00:03",
            "IPv4Address": "172.27.0.3/16",
            "IPv6Address": ""
        },
        "e0d5e0d03a07dfea11cd061097a3e1ef2fee6f851c282bff8b8a89d228a5194e": {
            "Name": "mysql",
            "EndpointID": "f20dd0ed478656e497c502d74541e2c57d30f27b45b0360f25ca766f89edd2e4",
            "MacAddress": "02:42:ac:1b:00:02",
            "IPv4Address": "172.27.0.2/16",
            "IPv6Address": ""
        }
    }
	```
	This shows us the ip of containers(mysql, nacos1, nacos2, nacos3) in docker.
	
	Ok, if I deploy MySQL `- port "3307:3306"`, my host reaches MySQL at 127.0.0.1:3307. Thinking of it, how does nacos1 in the docker container reach MySQL which is in another container? 3307 or 3306? YES ! 3306 is right ! So, let's check the nacos-hostname.env confiuration file. `NACOS_SERVERS=nacos1:8848 nacos2:8848 nacos3:8848` We use the hostname nacos1 instead of the real ip. The ports are also 8848 rather than 8849,8850.. so it is `MYSQL_SERVICE_PORT=3306`.
	
	How to know whether the services could communicate with each other? you can use ping utils in one contaniner. Like this:`ping ${antoher container ip adress}`, the ip address must be in docker network, such as docker-nacos_default above.
- If there has been a MySQL service in your docker container, you must put them(nacos1..3, MySQL) in the same network in order to communicate with each other.

## 1-4: Nginx Reverse Proxy
As mentioned above, the Nacos cluster won't be exposed to the outer environment. Each request reaches Nginx first, then Nginx dispatches requests to the Nacos cluster. In this article, I deploy nginx on my host, not docker. Yes, I failed to deploy it on the docker. The main reason is the network in docker. I put nginx on the same docker network `docker-nacos_default`. Many times I have tried I failed. QAQ. Fortunately, I realized my idea on my host machine-Ubuntu.You can install it by `apt-get install nginx` . Here is my config.
```xml
(base) ➜  docker-compose-nacos-mysql-master cd /etc/nginx 
(base) ➜  nginx ls
conf.d          koi-utf     modules-available  proxy_params     sites-enabled  win-utf
fastcgi.conf    koi-win     modules-enabled    scgi_params      snippets
fastcgi_params  mime.types  nginx.conf         sites-available  uwsgi_params
(base) ➜  nginx cat nginx.conf 
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
	worker_connections 768;
	# multi_accept on;
}

http {

	##
	# Basic Settings
	##

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;
	# server_tokens off;

	# server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# SSL Settings
	##

	ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
	ssl_prefer_server_ciphers on;

	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;

	# gzip_vary on;
	# gzip_proxied any;
	# gzip_comp_level 6;
	# gzip_buffers 16 8k;
	# gzip_http_version 1.1;
	# gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
    upstream nacos { 
      server  192.168.1.4:8848 weight=10; 
      server  192.168.1.4:8849 weight=10; 
      server  192.168.1.4:8850 weight=10; 
    } 
    server{ 
      listen 80; 
      server_name  192.168.1.4; 
      location / { 
          proxy_pass         http://nacos; 
      } 
    }
	##
	# Virtual Host Configs
	##

	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}
```
In my host, access nacos must from 192.168.1.4:8848; 192.168.1.4:8849; 192.168.1.4:8850; 192.168.1.4 is my ip. Nacos expose their internal port 8848 by 8848, 8849 and 8850 to the outside world. Like the picture below:
![在这里插入图片描述](https://img-blog.csdnimg.cn/af343be53cbf46e9838a53cb9f8788f0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_20,color_FFFFFF,t_70,g_se,x_16)
Success: Chrome access
> http://192.168.1.4/nacos/#/configurationManagement?dataId=&group=&appName=&namespace=&pageSize=&pageNo=

We can arrive nacos terminal.
![在这里插入图片描述](https://img-blog.csdnimg.cn/ed7b67ac69324813a88454789572f58f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_20,color_FFFFFF,t_70,g_se,x_16)
## 1-5: Reference
- [Install Nginx](https://zhuanlan.zhihu.com/p/138007915)
- [Change Apt Source in Docker Container](https://blog.csdn.net/j84491135/article/details/105938672?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~Rate-1.pc_relevant_paycolumn_v3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~Rate-1.pc_relevant_paycolumn_v3&utm_relevant_index=2)
- [MySQL master-servant + Nacos cluster + Nginx master-servant](https://blog.csdn.net/weixin_44790046/article/details/106857369#t6)
- [Gitee Deployment Written by a Coder](https://gitee.com/ysdxhsw/docker-compose-nacos-mysql)
- [Communication Between Containers](https://juejin.cn/post/6844903847383547911#comment)
- [Official Naco Group. There are examples of docker deployment in it.](https://github.com/nacos-group/nacos-docker)
- [Docker Cluster Deployment If You Has A MySQL Container Aleardy. i.e Different Docer Network Deployment](https://www.jianshu.com/p/c76832629062)
- [nacos-mysql.sql](https://github.com/alibaba/nacos/blob/master/distribution/conf/nacos-mysql.sql)
- [Nacos Cluster Deployment Document](https://nacos.io/zh-cn/docs/cluster-mode-quick-start.html)
