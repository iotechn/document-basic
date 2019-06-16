### CentOS 安装 Nginx 并配置 SSL

CentOS 下可直接使用 yum 安装 nginx

	yum install nginx

配置HTTPS需要先准备两个文件，也就是SSL证书的公私两部分。一般来说，大厂买的域名，都可以申请到免费的SSL证书。后缀分别为.key 和 .pem。

	1856198_fresh.easycampus.cn.key  1856198_fresh.easycampus.cn.pem

申请下来后本来在本机上面，如果本机是MacOS 或 Linux，可直接用scp拷贝到目标机上。如果是Windows通过xshell等终端工具连接的，可以使用zmodem传输。注：使用zmodem是要自己安装的。

	yum install lrzsz    //安装zmodem

反正自己想办法弄上去吧。不会的话加 QQ：944064365。

我们在 /etc/nginx 目录下再建一个目录 ssl，来存放证书。并使用mv将证书放进去ssl目录。
	
	cd /etc/nginx
	mkdir ssl

最后就是配置nginx了，没有道理可讲，请参照如下配置：

	vim /etc/nginx/nginx.conf

在http里面添加一个server，监听端口443，并指定好证书路径，location根据自己反向代理来定。

	server {
		listen 443;
		server_name localhost;
		ssl on;
		ssl_certificate /etc/nginx/ssl/1856198_fresh.easycampus.cn.pem;
		ssl_certificate_key /etc/nginx/ssl/1856198_fresh.easycampus.cn.key;
		ssl_session_timeout 5m;
		ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
		ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
		ssl_prefer_server_ciphers on;

		location / {
			proxy_pass http://localhost:8080/;
		}
	}

至此SSL配置完成 然后重新加载nginx即可。

	service nginx restart

