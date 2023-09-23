<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-09-18 14:59:01
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-09-18 16:25:12
 * @FilePath: \knowledge_planet\docs\md\Java\springboot.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### springboot

springboot 是一个开源的 java 框架用于创建独立的基于 spring 的应用程序，它简化了 spring 应用程序的配置和部署过程，并提供了很多开箱即用的功能和特性，使得开发人员可以更加关注业务逻辑的实现。

spring 的主要特点是：

1. 简化配置：spring boot 提供了自动配置的功能，通过约定大于配置的原则，大大减少了了显示配置的工作量。

2. 内嵌服务器： spring boot 可以将应用程序打包成可以执行的 jar 文件，并且内置了 Tomcat、Jetty 等服务器，不需要单独安装 Tomcat、Jetty 等服务器。

3. 自动装配：springboot 可以根据项目的依赖自动装配所需的 bean，不需要手动配置。

4. 外部化配置：springboot 可以根据配置文件进行外部的配置，可以使用属性文件、YAML 文件、环境变量等各种方式来配置应用程序的行为。

5. 健康监测：spring boot 提供了健康监测的功能，可以检查应用程序的运行状态，并提供相应的接口提供监测工具使用。

6. 简化测试：spring boot 提供了一些方便测试的工具，可以帮助开发人员编写单元测试和集成测试。

总之，springboot 提供了一次简单的、快速的开发环境，可以大大提高开发效率，并且适用各种规模的应用程序开发。

> ### 流程

1. 导入 starter-web：导入问开发场景

    - 场景启动器导入了相关场景的所有依赖：`start-json`、`starter-tomcat`、`spring-mvc`
    - 每个场景都引入了一个`spring-boot-starter`，核心场景启动器
    - 核心场景启动器导入了场景启动器，并导入了`spring-boot-autoconfigure`包
    - `spring-boot-autoconfigure`里面嵌括了所有场景的所有配置
    - 只要这个包下的所有类都能生效，那么相当于Springboot官方写好的整合功能就能生效

2. 主程序： `@SpringbootApplication`

```xml
<!-- 所有springboot项目都必须要继承这个spring-starter-parent -->
 <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.1.3</version>
    </parent>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.26</version>
        </dependency>
    </dependencies>

```
