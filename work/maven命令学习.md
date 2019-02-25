
Maven学习汇总
===

关注公众号"一束光阴的留恋" ，回复"全部",可以查看所有文章关键字。    
输入"`maven`、`maven命令`"，可快速查找到本文。



---
# 目录
* [环境变量](#环境变量)
* [命令](#目录)
    * [1.配置](#1.配置)
    * [2.创建](#2.创建)
    * [3.生产](#3.生产)
* [总结使用经验](#总结使用经验)
* [资源](#资源)

---
# 内容

##一、环境变量
```text
MAVEN_HOME=D:\Program Files\java\apache-maven-3.0.4
PATH=%MAVEN_HOME%\bin
```

测试命令`mvn -version`

![img](../images/Maven学习汇总.png)



## 二、命令

### 1.配置
* 查看版本`version`
> mvn -version/-v

* 显示详细错误信息
> mvn -e




### 2.创建

* 创建maven普通java项目`packageName` 报名，`projectName`项目名
> mvn archetype:create
      -DgroupId=packageName
      -DartifactId=projectName 
      [-DarchetypeArtifactId=maven-archetype-quickstart]

* 创建maven的web项目
> mvn archetype:create
      -DgroupId=packageName
      -DartifactId=webappName
      -DarchetypeArtifactId=maven-archetype-webapp

* 全自动提示创建maven项目
> mvn archetype:generate

全写写法
> mvn archetype:generate -DgroupId=com.xxx -DartifactId=Xxxxxx -Dversion=0.01-SNAPSHOT

详解：

![img](../images/maven-01.png)

需要输入的：

![img](../images/maven-02.png)


* 生成eclipse项目
> mvn eclipse:eclipse

* 生成idea项目
> mvn idea:idea



### 3.生产
* 编译
> mvn compile

* 编译测试代码
> mvn test-compile

* 运行测试
> mvn test

* 产生site
> mvn site

* 打包,生成target目录，编译、测试代码，生成测试报告，生成jar/war文件
> mvn package

* 打jar包
> mvn jar:jar

* 打包不测试
> mvn -Dtest package

* 清空缓存区
> men clean

* 清空缓存区，并打包新包
> mvn clean package
  
* 空缓存区，并打包新包，不验证测试用例
> mvn clean package -Dmaven.test.skip=true


* 打入本地仓库
> mvn install

* 清理项目
> mvn clean

* 只测试而不编译，也不测试编译
> mvn test -skipping compile -skipping test-compile

* 清理eclipse的一些系统设置
> mvn eclipse:clean 

* 查看当前项目已被解析的依赖
> mvn dependency:list

* 上传到私服
> mvn deploy

* 强制更新
> mvn clean install-U

* 源码打包：
> mvn source:jar   
> 或
> mvn source:jar-no-fork

* 运行项目于jetty上:
> mvn jetty:run


* 验证工程是否正确，所有需要的资源是否可用
> mvn -validate

* 在集成测试可以运行的环境中处理和发布包:

> mvn integration-test

* 运行任何检查，验证包是否有效且达到质量标准:
> mvn verify

* 下载项目关联的所有源代码
> mvn generate-sources

* help 插件的  describe 目标来输出 Maven Help 插件的信息:
> mvn help:describe -Dplugin=help

* Help 插件输出完整的带有参数的目标列 :
> mvn help:describe -Dplugin=help -Dfull



##三、总结使用经验
* mvn compile与mvn install、mvn deploy的区别
```
    mvn compile，编译类文件
    mvn install，包含mvn compile，mvn package，然后上传到本地仓库
    mvn deploy,包含mvn install,然后，上传到私服
```
























---
本文共学习使用，更多学习总结，扫一扫关注公众号

![img](../images/公众号.jpg)



动力源于生活，如果您觉得不错，可以支持我，感谢！
<center class="half">
    <img src="../images/收钱码-微信.png" width="200"/>
    <img src="../images/收钱码-支付宝.jpg" width="200"/>
</center>
