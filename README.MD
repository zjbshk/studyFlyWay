##### 首先是创建一个springboot的项目，pom.xml内容如下：
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>cn.infomany</groupId>
    <artifactId>studyFlyWay</artifactId>
    <version>1.0-SNAPSHOT</version>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.9.RELEASE</version>
        <relativePath/>
    </parent>

    <properties>
        <java.version>1.8</java.version>
    </properties>

    <dependencies>
        <!--   这个是flyway的核心，导入后springboot会自动进行管理，版本不是最新的    -->
        <dependency>
            <groupId>org.flywaydb</groupId>
            <artifactId>flyway-core</artifactId>
            <version>5.2.4</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

        <!--    java开发的工具包，使得类更加简洁    -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <!--    扩展插件，mybatis-plus，该依赖会自动导入mybatis    -->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.1.2</version>
        </dependency>
        <!--   连接mysql 驱动   -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.17</version>
        </dependency>
    </dependencies>


    <build>
        <plugins>
            <plugin>
                <groupId>org.flywaydb</groupId>
                <artifactId>flyway-maven-plugin</artifactId>
                <version>5.2.4</version>
            </plugin>
        </plugins>
    </build>
</project>
```

##### 然后再让我们看看`application.properties`文件：
```properties
server.port=8088
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/testdb?serverTimezone=UTC&useUnicode=true&characterEncoding=utf8&useSSL=false
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver


spring.jpa.hibernate.ddl-auto=none


#flyway.baseline-description对执行迁移时基准版本的描述.
#flyway.baseline-on-migrate当迁移时发现目标schema非空，而且带有没有元数据的表时，是否自动执行基准迁移，默认false.
#flyway.baseline-version开始执行基准迁移时对现有的schema的版本打标签，默认值为1.
#flyway.check-location检查迁移脚本的位置是否存在，默认false.
#flyway.clean-on-validation-error当发现校验错误时是否自动调用clean，默认false.
#flyway.enabled是否开启flywary，默认true.
#flyway.encoding设置迁移时的编码，默认UTF-8.
#flyway.ignore-failed-future-migration当读取元数据表时是否忽略错误的迁移，默认false.
#flyway.init-sqls当初始化好连接时要执行的SQL.
#flyway.locations迁移脚本的位置，默认db/migration.
#flyway.out-of-order是否允许无序的迁移，默认false.
#flyway.password目标数据库的密码.
#flyway.placeholder-prefix设置每个placeholder的前缀，默认${.
#flyway.placeholder-replacementplaceholders是否要被替换，默认true.
#flyway.placeholder-suffix设置每个placeholder的后缀，默认}.
#flyway.placeholders.[placeholder name]设置placeholder的value
#flyway.schemas设定需要flywary迁移的schema，大小写敏感，默认为连接默认的schema.
#flyway.sql-migration-prefix迁移文件的前缀，默认为V.
#flyway.sql-migration-separator迁移脚本的文件名分隔符，默认__
#flyway.sql-migration-suffix迁移脚本的后缀，默认为.sql
#flyway.tableflyway使用的元数据表名，默认为schema_version
#flyway.target迁移时使用的目标版本，默认为latest version
#flyway.url迁移时使用的JDBC URL，如果没有指定的话，将使用配置的主数据源
#flyway.user迁移数据库的用户名
#flyway.validate-on-migrate迁移时是否校验，默认为true.
```
![项目](https://upload-images.jianshu.io/upload_images/7473008-ab8fb416dab2e734.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可参考博客：
[https://www.jianshu.com/p/783b87871551](https://www.jianshu.com/p/783b87871551)
[https://blog.csdn.net/qiuhao9527/article/details/81070482](https://blog.csdn.net/qiuhao9527/article/details/81070482)

项目github位置如下：
[https://github.com/zjbshk/studyFlyWay](https://github.com/zjbshk/studyFlyWay)

