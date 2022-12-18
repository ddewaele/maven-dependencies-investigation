# Spring Boot Library

Imagine building a security library based on Spring Boot 2.7.1.

This would result in the following dependency tree :

As you can Spring Boot 2.7.1 relies on Spring Framework 5.3.21 and Spring Security 5.7.2 

```
[INFO] --- maven-dependency-plugin:3.3.0:tree (default-cli) @ spring-boot-lib ---
[INFO] com.example:spring-boot-lib:jar:0.0.1-SNAPSHOT
[INFO] \- org.springframework.boot:spring-boot-starter-oauth2-client:jar:2.7.1:compile
[INFO]    +- org.springframework.boot:spring-boot-starter:jar:2.7.1:compile
[INFO]    |  +- org.springframework.boot:spring-boot:jar:2.7.1:compile
[INFO]    |  +- org.springframework.boot:spring-boot-autoconfigure:jar:2.7.1:compile
[INFO]    |  +- org.springframework.boot:spring-boot-starter-logging:jar:2.7.1:compile
[INFO]    |  |  +- ch.qos.logback:logback-classic:jar:1.2.11:compile
[INFO]    |  |  |  +- ch.qos.logback:logback-core:jar:1.2.11:compile
[INFO]    |  |  |  \- org.slf4j:slf4j-api:jar:1.7.36:compile
[INFO]    |  |  +- org.apache.logging.log4j:log4j-to-slf4j:jar:2.17.2:compile
[INFO]    |  |  |  \- org.apache.logging.log4j:log4j-api:jar:2.17.2:compile
[INFO]    |  |  \- org.slf4j:jul-to-slf4j:jar:1.7.36:compile
[INFO]    |  +- jakarta.annotation:jakarta.annotation-api:jar:1.3.5:compile
[INFO]    |  +- org.springframework:spring-core:jar:5.3.21:compile
[INFO]    |  |  \- org.springframework:spring-jcl:jar:5.3.21:compile
[INFO]    |  \- org.yaml:snakeyaml:jar:1.30:compile
[INFO]    +- org.springframework.security:spring-security-config:jar:5.7.2:compile
[INFO]    |  +- org.springframework:spring-aop:jar:5.3.21:compile
[INFO]    |  +- org.springframework:spring-beans:jar:5.3.21:compile
[INFO]    |  \- org.springframework:spring-context:jar:5.3.21:compile
[INFO]    +- org.springframework.security:spring-security-core:jar:5.7.2:compile
[INFO]    |  +- org.springframework.security:spring-security-crypto:jar:5.7.2:compile
[INFO]    |  \- org.springframework:spring-expression:jar:5.3.21:compile
[INFO]    +- org.springframework.security:spring-security-oauth2-client:jar:5.7.2:compile
[INFO]    |  +- org.springframework.security:spring-security-oauth2-core:jar:5.7.2:compile
[INFO]    |  |  \- org.springframework:spring-web:jar:5.3.21:compile
[INFO]    |  +- org.springframework.security:spring-security-web:jar:5.7.2:compile
[INFO]    |  \- com.nimbusds:oauth2-oidc-sdk:jar:9.35:compile
[INFO]    |     +- com.github.stephenc.jcip:jcip-annotations:jar:1.0-1:compile
[INFO]    |     +- com.nimbusds:content-type:jar:2.2:compile
[INFO]    |     +- net.minidev:json-smart:jar:2.4.8:compile
[INFO]    |     |  \- net.minidev:accessors-smart:jar:2.4.8:compile
[INFO]    |     |     \- org.ow2.asm:asm:jar:9.1:compile
[INFO]    |     \- com.nimbusds:lang-tag:jar:1.6:compile
[INFO]    \- org.springframework.security:spring-security-oauth2-jose:jar:5.7.2:compile
[INFO]       \- com.nimbusds:nimbus-jose-jwt:jar:9.22:compile

```

If we were to package this library as a JAR file it would have the following dependencies

```
jar -tvf target/spring-boot-lib-0.0.1-SNAPSHOT.jar | grep BOOT-INF | awk '{print $8}'
BOOT-INF/
BOOT-INF/classes/
BOOT-INF/classes/com/
BOOT-INF/classes/com/example/
BOOT-INF/classes/com/example/demo/
BOOT-INF/classes/com/example/demo/DemoApplication.class
BOOT-INF/classes/application.properties
BOOT-INF/lib/
BOOT-INF/lib/spring-boot-2.7.1.jar
BOOT-INF/lib/spring-boot-autoconfigure-2.7.1.jar
BOOT-INF/lib/logback-classic-1.2.11.jar
BOOT-INF/lib/logback-core-1.2.11.jar
BOOT-INF/lib/slf4j-api-1.7.36.jar
BOOT-INF/lib/log4j-to-slf4j-2.17.2.jar
BOOT-INF/lib/log4j-api-2.17.2.jar
BOOT-INF/lib/jul-to-slf4j-1.7.36.jar
BOOT-INF/lib/jakarta.annotation-api-1.3.5.jar
BOOT-INF/lib/spring-core-5.3.21.jar
BOOT-INF/lib/spring-jcl-5.3.21.jar
BOOT-INF/lib/snakeyaml-1.30.jar
BOOT-INF/lib/spring-security-config-5.7.2.jar
BOOT-INF/lib/spring-aop-5.3.21.jar
BOOT-INF/lib/spring-beans-5.3.21.jar
BOOT-INF/lib/spring-context-5.3.21.jar
BOOT-INF/lib/spring-security-core-5.7.2.jar
BOOT-INF/lib/spring-security-crypto-5.7.2.jar
BOOT-INF/lib/spring-expression-5.3.21.jar
BOOT-INF/lib/spring-security-oauth2-client-5.7.2.jar
BOOT-INF/lib/spring-security-oauth2-core-5.7.2.jar
BOOT-INF/lib/spring-web-5.3.21.jar
BOOT-INF/lib/spring-security-web-5.7.2.jar
BOOT-INF/lib/oauth2-oidc-sdk-9.35.jar
BOOT-INF/lib/jcip-annotations-1.0-1.jar
BOOT-INF/lib/content-type-2.2.jar
BOOT-INF/lib/json-smart-2.4.8.jar
BOOT-INF/lib/accessors-smart-2.4.8.jar
BOOT-INF/lib/asm-9.1.jar
BOOT-INF/lib/lang-tag-1.6.jar
BOOT-INF/lib/spring-security-oauth2-jose-5.7.2.jar
BOOT-INF/lib/nimbus-jose-jwt-9.22.jar
BOOT-INF/lib/spring-boot-jarmode-layertools-2.7.1.jar
BOOT-INF/classpath.idx
BOOT-INF/layers.idx
```


However, if we were to embed this security library into a project based on spring boot 2.7.6 we would get this

(notice how all the 5.7.2 files from the security library have now been automatically upgraded to 5.7.6)
```
BOOT-INF/
BOOT-INF/classes/
BOOT-INF/classes/com/
BOOT-INF/classes/com/example/
BOOT-INF/classes/com/example/demo/
BOOT-INF/classes/com/example/demo/DemoApplication.class
BOOT-INF/classes/application.properties
BOOT-INF/lib/
BOOT-INF/lib/spring-boot-2.7.6.jar
BOOT-INF/lib/spring-boot-autoconfigure-2.7.6.jar
BOOT-INF/lib/logback-classic-1.2.11.jar
BOOT-INF/lib/logback-core-1.2.11.jar
BOOT-INF/lib/log4j-to-slf4j-2.17.2.jar
BOOT-INF/lib/log4j-api-2.17.2.jar
BOOT-INF/lib/jul-to-slf4j-1.7.36.jar
BOOT-INF/lib/jakarta.annotation-api-1.3.5.jar
BOOT-INF/lib/snakeyaml-1.30.jar
BOOT-INF/lib/spring-aop-5.3.24.jar
BOOT-INF/lib/spring-beans-5.3.24.jar
BOOT-INF/lib/spring-security-config-5.7.5.jar
BOOT-INF/lib/spring-security-core-5.7.5.jar
BOOT-INF/lib/spring-security-crypto-5.7.5.jar
BOOT-INF/lib/spring-context-5.3.24.jar
BOOT-INF/lib/spring-security-web-5.7.5.jar
BOOT-INF/lib/spring-expression-5.3.24.jar
BOOT-INF/lib/spring-web-5.3.24.jar
BOOT-INF/lib/spring-boot-lib-0.0.1-SNAPSHOT.jar
BOOT-INF/lib/spring-security-oauth2-client-5.7.5.jar
BOOT-INF/lib/spring-security-oauth2-core-5.7.5.jar
BOOT-INF/lib/oauth2-oidc-sdk-9.35.jar
BOOT-INF/lib/jcip-annotations-1.0-1.jar
BOOT-INF/lib/content-type-2.2.jar
BOOT-INF/lib/lang-tag-1.6.jar
BOOT-INF/lib/spring-security-oauth2-jose-5.7.5.jar
BOOT-INF/lib/nimbus-jose-jwt-9.22.jar
BOOT-INF/lib/json-smart-2.4.8.jar
BOOT-INF/lib/accessors-smart-2.4.8.jar
BOOT-INF/lib/asm-9.1.jar
BOOT-INF/lib/slf4j-api-1.7.36.jar
BOOT-INF/lib/spring-core-5.3.24.jar
BOOT-INF/lib/spring-jcl-5.3.24.jar
BOOT-INF/lib/spring-boot-jarmode-layertools-2.7.6.jar
BOOT-INF/classpath.idx
BOOT-INF/layers.idx

```