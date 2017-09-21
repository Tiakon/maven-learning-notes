# Maven Learning Notes
Take notes that are recorded whenlearning Maven in imooc

Maven学习笔记
=========


----------
一.介绍
----
**Maven**是基于项目对象模型（POM），可以通过一小段描述信息来管理项目的构建、报告和文档的软件项目管理工具。

1. bin目录是包含mvn的运行脚本
2. boot目录包含一个类加载器的框架，maven使用它加载自己的类库
3. conf配置文件
4. lib包含maven运行时的依赖类库

二.环境变量的配置
---------
[点击下载](http://maven.apache.org/download.cgi "下载地址")<br>
**maven**环境配置，增加一个环境变量**MAVEN_HOME**,值是maven的安装路径（`C:\Program Files\apache-maven-3.5.0-bin\apache-maven-3.5.0`）
修改path则是在path最后面添加`;%MAVEN_HOME%\bin`。

### Maven的项目结构 ###
	
	项目名
		-src 
		   -main
		        -java
		             -package
		   -test
		        -java
		             -package
		-pom.xml

三.常用命令
------
    mvn -v 			查看maven版本
    	 compile	编译
    	 test		测试
    	 package	打包
    
    	 clean		删除target
    	 install	安装jar包到本地仓库

### maven快速创建项目骨架目录  ###
#### 两种方式： ####
	1.  mvn archetype:generate 按照提示进行选择
	2.  mvn archetype:generate  -DgroupId=com.imooc.maven   -DartifactId=
	  maven-service   -Dversion=1.0.0SNAPSHOT   -Dpackage=com.imooc.maven.demo
		1. -DgroupId=组织名，公司网址反写+项目名
		2. -DartifactId=项目名+模块名
		3. -Dversion=版本号
		4. -Dpackage=代码所存在的包名
四.Maven中的坐标和仓库
--------------

**构件坐标:**

	    	1. groupId:公司名字+项目名
	    	2. artifactId：项目名+模块名
	    	3. varsion:版本号

**仓库：**

			1. 本地仓库
			2. 远程仓库
			3. 镜像仓库

更改仓库默认路径
------
已安装到本地仓库中的jar包位置：

    C:\Users\用户\.m2\repository\com\tiakon\demo

安装路径conf文件夹下settings.xml文件
打开找到这段备注是的代码：
      
		  <!-- localRepository
		   | The path to the local repository maven will use to store artifacts.
		   | Default: ${user.home}/.m2/repository
		  <localRepository>/path/to/local/repo</localRepository>
		  -->

复制粘贴出来

		<localRepository>/path/to/local/repo</localRepository>

**将localRepository便签内的值替换成新路径即可。**

maven生命周期
---------

完整的项目构建过程包括：
	
**清理、编译、测试、打包、集成测试、验证、部署**

**maven三套独立的生命周期**

    	clean 	清理项目
    			1.pre-clean		执行清理前的工作
    			2.clean			清理上一次构建生成的所有文件
    			3.post-clean 	执行清理后的文件
    
    	default 构建项目（最核心）
    			compile test package install
    
    	site 	生成项目站点
    			1. pre-site 	在生成项目站点前要完成的工作
    			2. site 		生成项目的站点文档
    			3. post-site	在生成项目站点后要完成的工作
    			4. site-deploy	发布生成的站点到服务器上
			
