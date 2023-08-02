<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-15 13:52:42
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-08-02 11:24:41
 * @FilePath: \knowledge_planet\docs\md\Jenkins\Jenkins.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### jenkins 是什么？

jenkins 是一个流行的自动化服务器，用于自动化构建、部署、测试软件项目

jenkins 提供了丰富的插件生态系统，可以帮助用户在不同平台和技术栈下轻松的构建和管理软件项目

被广泛运用在软件开发和 devOps 领域

> ### jenkins 搭建

前期准备：已购有服务器、宝塔面板

> ### 宝塔面板安装 docker 插件

![Alt text](image.png)

> ### docker 拉取 jenkins 镜像

```dash
docker pull jenkins/jenkins:lts
```

-   查看 docker 容器下的镜像列表，查看 jenkins 镜像是否拉取成功

```dash
docker images
```

![Alt text](image-1.png)

-   在首页打开 docker 管理器

![Alt text](image-2.png)

-   创建容器 - 选择我们刚才下载的 jenkins 镜像 - 端口映射 将容器端口和服务器端口都填为 8080 以及对外开放端口号

        ```dash
            docker run -d -p 8080:8080 jenkins/jenkins:lts
        ```
        - 目录映射 容器目录为jenkins  服务器目录为jenkins_home

    ![Alt text](image-3.png)

最后点击提交完成容器创建

![Alt text](image-4.png)

-   创建站点

将指定已经解析的域名指向该站点

![Alt text](image-6.png)

点击设置

![Alt text](image-7.png)

添加反向代理

![Alt text](image-8.png)

![Alt text](image-9.png)

最后在浏览器上打开你指定的域名可以了 xxxx.com
![Alt text](image-10.png)

出现此页面就代表你 docker 部署 jenkins 成功了
