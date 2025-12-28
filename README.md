# data_platform_web
数采平台

1.部署前端
  1）安装nginx
  	sudo apt update
  	sudo apt install nginx
  2）启动nginx
  	sudo systemctl start nginx
  3) 配置nginx端口：
  	cd /etc/nginx/conf.d/
  	sudo -E vi dataplatform.conf
	"""
	server {
    	listen 8000;
    	server_name localhost;
    	location / {
        	root /var/www/html/fastumi_data_platform_frontend;
        	index index.html index.htm;
        	try_files $uri $uri/ = 404;
    		}

	}
	"""
  4）重新加载nginx配置:
   	sudo -E nginx -s reload
  5）将data_platform_frontend复制到/var/www/html下：
  	cd /var/www/html
  	sudo -E cp -r /实际路径/data_platform_deploy/fastumi_data_platform_frontend .
  	
访问http://localhost:8000 
用户名:admin
密码:admin123    

*关闭nginx：sudo systemctl stop nginx


2.部署后端
  1）赋可执行权限:
  	chmod +x fastumi_data_platform_backend
  2）启动服务:
  	./fastumi_data_platform_backend
