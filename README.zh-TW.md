[English](README.md) | [簡體中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

# 資源處理器 Spring Boot Starter

讓 Spring Boot 應用快速整合限流能力，防止訪問過於頻繁。

## 快速開始

- 匯入相依性

```xml
    <dependency>
        <groupId>com.jiovan.spring.starter</groupId>
        <artifactId>resource-handler-spring-boot-starter</artifactId>
        <version>LATEST</version>
    </dependency>
```

> 預設情況下，此 starter 會自動生效，你可以透過 `jiovan.resource-handler.enabled = false` 關閉它。

- 使用字首 `jiovan.resource-handler` 設定 Spring Boot 的 `application.yml`（**可選**）

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

- **可選功能**：如果你不希望把大量檔案直接放在 `src/main/resources` 目錄下，不妨試試 `virtual-root` 功能。它會在 `original` 對映中新增虛擬對映 "/vroot/**"，這樣你就可以把檔案放在 `src/main/resources/vroot` 目錄下，然後透過 `://domain/file` 訪問它們。這對 `favicon.ico`、`robot.txt` 等檔案非常有用。

- 在（非靜態）方法上標註 `@RateLimited` 註解即可！

> 註解的 `keyType` 屬性表示限流方式，支援
  - IP 地址
  - 會話
  - 使用者名稱

- 此 starter 需要將限流資料儲存到某處，目前支援
  - redis

## 文件

- GitHub：https://github.com/jiovan-labs/resource-handler-spring-boot-starter

## 環境要求

- jdk 17+

## 許可證

本專案採用 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) 許可證。

請參閱 `NOTICE.txt` 檔案瞭解所需的宣告與歸屬資訊。

## 捐贈

喜歡這個工具包嗎？歡迎[向我們捐贈](https://jiovan.com/donation)以支援開發。

## 版權

北京玖漫科技有限公司

## 網站

- 玖漫：https://jiovan.com
