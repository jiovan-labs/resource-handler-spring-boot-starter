[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

# 资源处理器 Spring Boot Starter

让 Spring Boot 应用快速集成限流能力，防止访问过于频繁。

## 快速开始

- 导入依赖

```xml
    <dependency>
        <groupId>com.jiovan.spring.starter</groupId>
        <artifactId>resource-handler-spring-boot-starter</artifactId>
        <version>LATEST</version>
    </dependency>
```

> 默认情况下，此 starter 会自动生效，你可以通过 `jiovan.resource-handler.enabled = false` 关闭它。

- 使用前缀 `jiovan.resource-handler` 配置 Spring Boot 的 `application.yml`（**可选**）

```yml
jiovan:
    resource-handler:
        resource-mapping:
            add-default-versional: true
            add-default-original: false
            versional:
                - '/foo/**': 'classpath:/foo/'
            original:
                - '/bar/**': 'classpath:/bar/'
        virtual-root:
            resource: 'classpath:/vroot/'
```

- **可选功能**：如果你不希望把大量文件直接放在 `src/main/resources` 目录下，不妨试试 `virtual-root` 功能。它会在 `original` 映射中添加虚拟映射 "/vroot/**"，这样你就可以把文件放在 `src/main/resources/vroot` 目录下，然后通过 `://domain/file` 访问它们。这对 `favicon.ico`、`robot.txt` 等文件非常有用。

- 在（非静态）方法上标注 `@RateLimited` 注解即可！

> 注解的 `keyType` 属性表示限流方式，支持
  - IP 地址
  - 会话
  - 用户名

- 此 starter 需要将限流数据保存到某处，目前支持
  - redis

## 文档

- GitHub：https://github.com/jiovan-labs/resource-handler-spring-boot-starter

## 环境要求

- jdk 17+

## 许可证

本项目采用 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) 许可证。

请参阅 `NOTICE.txt` 文件了解所需的声明与归属信息。

## 捐赠

喜欢这个工具包吗？欢迎[向我们捐赠](https://jiovan.com/donation)以支持开发。

## 版权

北京玖漫科技有限公司

## 网站

- 玖漫：https://jiovan.com
