### CentOS 安装 Maven
首先在/root/目录下创建downloads目录，并cd进去
	
	cd
	mkdir downloads
	cd downloads

然后使用wget命令从官网下载Maven

	wget http://mirror.bit.edu.cn/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz

下载完成后，使用tar命令解压maven

	tar -zxvf apache-maven-3.6.1-bin.tar.gz

将解压完成的文件夹移动到/root/目录下

	mv apache-maven-3.6.1 ../

创建软链接
	
	ln -s apache-maven-3.6.1/ maven

配置环境变量
	
	vim ~/.bashrc

在.bashrc文件后追加以下文本

	export MAVEN_HOME='/root/maven'
	export PATH=$PATH:$MAVEN_HOME/bin

使用source命令刷新，并使用which命令校验是否配置完成

	source ~/.bashrc
	which mvn

出现路径，表示已经配好了。若出现 no mvn in (xxxx) 表示没配置好。到此maven安装完成。