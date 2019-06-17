### CentOS 安装 NodeJs 8.15.0

安装前先cd进下载目录,并用wget下载包，其他版本可去[官方网站](https://nodejs.org/en/download/releases/)上查找。

	cd ~/downloads
	wget https://nodejs.org/download/release/v8.15.0/node-v8.15.0-linux-x64.tar.gz

用tar命令解压压缩包，并将解压得到的文件夹移动到 /root/

	tar -zxvf node-v8.15.0-linux-x64.tar.gz 
	mv node-v8.15.0-linux-x64 ../

然后创建软链接
	
	cd 
	ln -s node-v8.15.0-linux-x64/ node

配置环境变量，使node可以在任何地方被使用。
	
	vim .bashrc
	
在.bashrc末尾添加下这两行文本

	export NODE_HOME='/root/node'
	export PATH=$PATH:$NODE_HOME/bin

保存后退出，并用source命令刷新，并用which命令来查看是否配置完成
	
	source .bashrc
	which node

若出现目录，则配置完成。若出现 no node in (xxxx) 表示没配置好。到此nodejs安装完成。nodejs会自带npm。

安装完nodejs后。我们可以安装一个cnpm来提高依赖下载速度，使用cnpm后依赖下载会走淘宝的源。

	npm install -g cnpm --registry=https://registry.npm.taobao.org

A few years later 就可以了，使用cnpm速度可以提升很多。
