### CentOS 安装 JDK8

首先在/root/目录下创建downloads目录，并cd进去
	
	cd
	mkdir downloads
	cd downloads

然后使用wget命令从Oracle下载JDK8
	
	wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u141-b15/336fa29ff2bb4ef291e347e091f7f4a7/jdk-8u141-linux-x64.tar.gz"

下载完成后使用tar命令解压

	tar -zxvf jdk-8u141-linux-x64.tar.gz

将解压出来的文件夹移动到/root/目录下，并创建软链接
	
	mv jdk1.8.0_141/ ../
	cd
	ln -s jdk1.8.0_141/ jdk

然后配置JAVA_HOME和PATH环境变量

	vim ~/.bashrc

在.bashrc末尾追加

	export JAVA_HOME='/root/jdk'
	export PATH=$PATH:$JAVA_HOME/bin

使用source命令刷新环境变量配置
	
	source ~/.bashrc

并使用which来查看是否配好
	
	which javac

出现路径，表示已经配好了。若出现 no javac in (xxxx) 表示没配置好。到此jdk安装完成。
