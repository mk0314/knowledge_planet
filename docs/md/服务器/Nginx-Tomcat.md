> ### Nginx

Nginx 是一个高性能的开源反向代理服务器和 Web 服务器。它以优异的性能、高并发处理能力和低内存消耗而闻名。

> ### Nginx 特点和用途

-   反向代理： Nginx 可以作为反向代理，将请求转发给后端的多个服务器，实现负载均衡，提高系统的性能和和可靠性。

-   静态文件服务：Nginx 也可以作为静态文件服务器，提供静态文件，例如图片、视频、音频等。

-   压缩： Nginx 支持对静态文件进行压缩，可以显著提高传输效率。

-   缓存： Nginx 支持对静态文件进行缓存，可以显著提高响应速度。

-   SSL/TLS 加密支持： Nginx 可以配置和管理 SSL/TLS 证书，实现安全的 HTTPS 连接。

-   URL 重定向和重写： Nginx 支持灵活的 URL 重写和重定向规则，可以实现 URL 重定向和 URL 重写。

-   动态请求代理：Nginx 可以与后端的应用服务器（如 php、python 或 node.js）配合使用，代理动态请求。

-   高并发处理：Nginx 在高并发表现优异，可以支持超过百万级的并发连接。

-   低内存消耗：Nginx 采用内核和用户空间分离的设计，使得 Nginx 消耗的内存非常低。

-   可扩展性： nginx 可以通过添加模块和插件进行扩展，满足特定需求。

```js
server
{
    listen 80;
		listen 443 ssl http2;
    server_name doc.mkook.xyz;
    index index.php index.html index.htm default.php default.htm default.html;
    root /www/wwwroot/doc.mkook.xyz;

    #SSL-START SSL相关配置，请勿删除或修改下一行带注释的404规则
    #error_page 404/404.html;
    ssl_certificate    /www/server/panel/vhost/cert/doc.mkook.xyz/fullchain.pem;
    ssl_certificate_key    /www/server/panel/vhost/cert/doc.mkook.xyz/privkey.pem;
    ssl_protocols TLSv1.1 TLSv1.2 TLSv1.3;
    ssl_ciphers EECDH+CHACHA20:EECDH+CHACHA20-draft:EECDH+AES128:RSA+AES128:EECDH+AES256:RSA+AES256:EECDH+3DES:RSA+3DES:!MD5;
    ssl_prefer_server_ciphers on;
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 10m;
    add_header Strict-Transport-Security "max-age=31536000";
    error_page 497  https://$host$request_uri;

    #SSL-END

    #ERROR-PAGE-START  错误页配置，可以注释、删除或修改
    #error_page 404 /404.html;
    #error_page 502 /502.html;
    #ERROR-PAGE-END

    #PHP-INFO-START  PHP引用配置，可以注释或修改
    include enable-php-00.conf;
    #PHP-INFO-END

    #REWRITE-START URL重写规则引用,修改后将导致面板设置的伪静态规则失效
    include /www/server/panel/vhost/rewrite/doc.mkook.xyz.conf;
    #REWRITE-END

    #禁止访问的文件或目录
    location ~ ^/(\.user.ini|\.htaccess|\.git|\.env|\.svn|\.project|LICENSE)
    {
        return 404;
    }

    #一键申请SSL证书验证目录相关设置
    location ~ \.well-known{
        allow all;
    }

    #禁止在证书验证目录放入敏感文件
    if ( $uri ~ "^/\.well-known/.*\.(php|jsp|py|js|css|lua|ts|go|zip|tar\.gz|rar|7z|sql|bak)$" ) {
        return 403;
    }

    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
    {
        expires      30d;
        error_log /dev/null;
        access_log /dev/null;
    }

    location ~ .*\.(js|css)?$
    {
        expires      12h;
        error_log /dev/null;
        access_log /dev/null;
    }
    access_log  /www/wwwlogs/doc.mkook.xyz.log;
    error_log  /www/wwwlogs/doc.mkook.xyz.error.log;
}
```

总体而言，Nginx 是一个灵活、高性能的服务器软件， 适用于构建可靠的、高效的 web 应用程序和服务，他可以被广泛应用于大型网站个应用程序中，具备良好的稳定性和可靠性。

> ### Tomcat

Tomcat 是一个开源的 Java Servlet 容器，可以处理 HTTP 请求。同时也支持 javaServer Pages（JSP）和相关的 Java EE 技术。

> ### Tomcat 特点和用途

-   servlet 容器： Tomcat 可以执行和管理 java Servlet，这是 java web 应用程序的基本组件，用于处理动态请求和生成动态内容。

-   JSP 引擎：Tomcat 提供了对 JavaServer Page(JSP) 的支持， 它是一种模块引擎，用于创建动态请求和生成动态内容。

-   Java EE 支持： Tomcat 部分实现了 java EE 规范， 包括支持 java Servlet、javaServer Pages、Java Expression Language、Java Remote Method Invocation、XML Web Services、Java Message Service、Java EJB、JavaMail、Java Web 等技术。

-   Web 应用容器: Tomcat 可以托管并运行多个独立的 web 应用程序，每个应用程序都有自己的配置文件，可以单独启动和关闭。

-   配置灵活： Tomcat 提供了丰富的配置选项，可以自定义端口、域名、路径、安全配置、日志记录等。

-   安全性管理： Tomcat 支持用户身份验证和访问验证，可以限制对 web 应用程序的访问。

-   支持集群：可以部署多个 Tomcat 实例，每个实例运行在不同的端口上，可以通过负载均衡器将请求分发到不同的实例上。

tomcat 配置

```xml

<?xml version="1.0" encoding="UTF-8"?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<!-- Note:  A "Server" is not itself a "Container", so you may not
     define subcomponents such as "Valves" at this level.
     Documentation at /docs/config/server.html
 -->
<Server port="8005" shutdown="SHUTDOWN">
  <Listener className="org.apache.catalina.startup.VersionLoggerListener" />

  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />
  <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" />


  <GlobalNamingResources>

    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
  </GlobalNamingResources>


  <Service name="Catalina">


    <Connector port="80" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443"
			   maxHttpHeaderSize ="20000" />
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />



    <Engine name="Catalina" defaultHost="localhost">


      <Realm className="org.apache.catalina.realm.LockOutRealm">

        <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
               resourceName="UserDatabase"/>
      </Realm>

      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">



		<Context docBase="/cnas/fontEnd" path="/" reloadable="true" source=""/>

        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />

      </Host>
    </Engine>
  </Service>

    <!-- doc -->

   <Service name="Catalina">


    <Connector port="8686" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443"
			   maxHttpHeaderSize ="20000" />
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />



    <Engine name="Catalina" defaultHost="localhost">


      <Realm className="org.apache.catalina.realm.LockOutRealm">

        <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
               resourceName="UserDatabase"/>
      </Realm>

      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">

		<Context docBase="/doc" path="/" reloadable="true" source=""/>

        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />
      </Host>
    </Engine>
  </Service>
</Server>


```

总而言之,Tomcat 是一个可靠的 Java Web 应用服务器， 被广泛应用于开发和部署 java web 应用程序。

> ### Nginx 于 Tomcat 区别

Nginx 和 Tomcat 都是我们常见的 web 服务器软件，他们在功能和用途上都有很多相似之处，下面我们来对比一下他们的区别。

1. Nginx 处理静态文件好，而 Tomcat 处理 JSP 或 Servlet 应用好。

2. Nginx 处理动态请求速度快，而 Tomcat 处理静态文件速度快。

3. Nginx 占用系统资源少，而 Tomcat 占用系统资源多。

4. Nginx 适合高并发，而 Tomcat 适合低并发。

5. Nginx 适合做反向代理，而 Tomcat 适合做应用服务器。

6. Nginx 适合做负载均衡，而 Tomcat 适合做集群。

7. Nginx 适合做缓存，而 Tomcat 适合做应用服务器。

8. Nginx 适合做虚拟主机，而 Tomcat 适合做应用服务器。

9. Nginx 相对于 Tomcat 来说单线程比多线程的效率要高， 而且更加轻量级。
