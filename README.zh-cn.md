angularjs-springmvc-sample-boot
===============================

采用 AnguarJS/Bootstrap 作为前端，Spring MVC 提供 REST API 的一个示例程序。

**更详细的内容, 请在线阅读 GitBook: [Building REST APIs with Spring MVC](https://www.gitbook.com/book/hantsy/build-a-restful-app-with-spring-mvc-and-angularjs/details).**



技能栈:

* Spring Boot
* Spring MVC
* Spring Data JPA
* JPA
* Hibernate 5.2
* Spring Security
* Swagger/Swagger2Markup/Spring Rest Docs
* Spring Test/JUnit/Mockito/JBehave/RestAssured
* Lombok
* ModelMapper
* AngularJS
* Bootstrap

这个版本增强了 [原始版本(未使用 Spring Boot)](https://github.com/hantsy/angularjs-springmvc-sample), 内容包括:

* 介绍 Gulp 构建系统处理静态资源
* 前端 UI 可独立采用 NodeJS 生态系统运行
* 提供一个选项可把静态资源打包成 final jar 的一部分，直接用命令 `mvn spring-boot:run` 运行

## 环境需求

* JDK 8

  Oracle Java 8 是必须的, 请前往[Oracle Java website](http://java.oracle.com) 下载安装进你的系统
 
  可选, 你可以设置 **JAVA\_HOME** 进环境变量和添加 *&lt;JDK installation dir>/bin* 去 **PATH** 的环境变量

* Apache Maven

  下载 Apache Maven 最新版本 [http://maven.apache.org](http://maven.apache.org), 然后在本地进行解压

  可选, 你可以设置 **M2\_HOME** 进环境变量，不要忘记添加 *&lt;Maven Installation dir>/bin* 进 **PATH** 的环境变量

* NodeJS

  NodeJS 是必须的，它用来构建前端静态文件
 
  下载 [NodeJS](http://nodejs.org) 后本地安装
 
  下载完之后打开终端输入 `node -v` 命令来确认安装配置成功
 
  ```
  node -v 
  >v4.2.2
  ```
 
  `bower` 也是必须的运行时依赖, `gulp` 用来作为我们的构建静态资源的工具
 
  ```
  npm install -g bower
  npm install -g gulp
  ```
 
## 获取源代码

拉取一份源代码到你的本地

```
git clone https://github.com/hantsy/angularjs-springmvc-sample-boot
```

## 运行源代码

你可以选取其中之一来运行该代码

### 分别运行前后端

1. Spring Boot 来运行后端 API 服务器

   ```
   mvn spring-boot:run
   ```

   后端 APIs 将运行在端口 9000.

2. 独立的运行前端
   
   ```
   npm install
   bower install
   gulp serve
   ```

   默认情况下, gulp 提供前端服务在端口 3000.

3. 浏览器打开 [http://localhost:3000](http://localhost:3000) 去测试

### Run the project via Spring Boot maven plugin
     
1. Run the following command to resovle the dependencies of the frontend static resources.
   
   ```
   npm install
   bower install
   ```

2. Run the backend API server with `spring-boot` command. The parameter `-Dstatic-ui` will copy the static resources and package into the jar archive.

   ```
   mvn spring-boot:run -Dstatic-ui
   ```

3. Go to [http://localhost:9000](http://localhost:9000) to test it. 

If you want to explore the REST API docs online, there is a *Swagger UI* configured for visualizing the REST APIs, just go to [http://localhost:9000/swagger-ui.html](http://localhost:9000/swagger-ui.html).
 
### Generate static REST API reference documentation

I have moved the REST docs generation configuration into a standalone Maven profile.

Execute the following command to generate HTML and PDF format files for your REST APIs from Swagger API description file and Spring test code snippets(as code samples).

```
mvn clean package -Drestdocs
```

The detailed configuration is explained in [API documention](https://hantsy.gitbooks.io/build-a-restful-app-with-spring-mvc-and-angularjs/content/swagger.html) section.

When it is done, check the generated static docs in *target/asciidoc* folder, it includes a HTML 5 file(under html folder), and a PDF file(in pdf folder).

Open the pdf document in Adobe Reader, it looks like.

![pdf](https://github.com/hantsy/angularjs-springmvc-sample-boot/blob/master/restdocs.png) 
 
### Docker

You can run the project in multistage Docker building development environment, check [Multistage Builds](https://github.com/hantsy/devops-sandbox/blob/master/multistage.md).