# Maven Dependency Investigation

Lets start by looking at our verbose dependency tree, created with `mvn dependency:tree`

```
[INFO] Scanning for projects...
[INFO]
[INFO] -------------------< com.example:spring-boot-2.7.6 >--------------------
[INFO] Building demo 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-dependency-plugin:3.3.0:tree (default-cli) @ spring-boot-2.7.6 ---
[INFO] com.example:spring-boot-2.7.6:jar:0.0.1-SNAPSHOT
[INFO] +- org.springframework.boot:spring-boot-starter:jar:2.7.6:compile
[INFO] |  +- org.springframework.boot:spring-boot:jar:2.7.6:compile
[INFO] |  |  \- org.springframework:spring-context:jar:5.3.24:compile
[INFO] |  |     +- org.springframework:spring-aop:jar:5.3.24:compile
[INFO] |  |     +- org.springframework:spring-beans:jar:5.3.24:compile
[INFO] |  |     \- org.springframework:spring-expression:jar:5.3.24:compile
[INFO] |  +- org.springframework.boot:spring-boot-autoconfigure:jar:2.7.6:compile
[INFO] |  +- org.springframework.boot:spring-boot-starter-logging:jar:2.7.6:compile
[INFO] |  |  +- ch.qos.logback:logback-classic:jar:1.2.11:compile
[INFO] |  |  |  \- ch.qos.logback:logback-core:jar:1.2.11:compile
[INFO] |  |  +- org.apache.logging.log4j:log4j-to-slf4j:jar:2.17.2:compile
[INFO] |  |  |  \- org.apache.logging.log4j:log4j-api:jar:2.17.2:compile
[INFO] |  |  \- org.slf4j:jul-to-slf4j:jar:1.7.36:compile
[INFO] |  +- jakarta.annotation:jakarta.annotation-api:jar:1.3.5:compile
[INFO] |  +- org.springframework:spring-core:jar:5.3.24:compile
[INFO] |  |  \- org.springframework:spring-jcl:jar:5.3.24:compile
[INFO] |  \- org.yaml:snakeyaml:jar:1.30:compile
[INFO] \- org.springframework.boot:spring-boot-starter-test:jar:2.7.6:test
[INFO]    +- org.springframework.boot:spring-boot-test:jar:2.7.6:test
[INFO]    +- org.springframework.boot:spring-boot-test-autoconfigure:jar:2.7.6:test
[INFO]    +- com.jayway.jsonpath:json-path:jar:2.7.0:test
[INFO]    |  +- net.minidev:json-smart:jar:2.4.8:test
[INFO]    |  |  \- net.minidev:accessors-smart:jar:2.4.8:test
[INFO]    |  |     \- org.ow2.asm:asm:jar:9.1:test
[INFO]    |  \- org.slf4j:slf4j-api:jar:1.7.36:compile
[INFO]    +- jakarta.xml.bind:jakarta.xml.bind-api:jar:2.3.3:test
[INFO]    |  \- jakarta.activation:jakarta.activation-api:jar:1.2.2:test
[INFO]    +- org.assertj:assertj-core:jar:3.22.0:test
[INFO]    +- org.hamcrest:hamcrest:jar:2.2:test
[INFO]    +- org.junit.jupiter:junit-jupiter:jar:5.8.2:test
[INFO]    |  +- org.junit.jupiter:junit-jupiter-api:jar:5.8.2:test
[INFO]    |  |  +- org.opentest4j:opentest4j:jar:1.2.0:test
[INFO]    |  |  +- org.junit.platform:junit-platform-commons:jar:1.8.2:test
[INFO]    |  |  \- org.apiguardian:apiguardian-api:jar:1.1.2:test
[INFO]    |  +- org.junit.jupiter:junit-jupiter-params:jar:5.8.2:test
[INFO]    |  \- org.junit.jupiter:junit-jupiter-engine:jar:5.8.2:test
[INFO]    |     \- org.junit.platform:junit-platform-engine:jar:1.8.2:test
[INFO]    +- org.mockito:mockito-core:jar:4.5.1:test
[INFO]    |  +- net.bytebuddy:byte-buddy:jar:1.12.19:test
[INFO]    |  +- net.bytebuddy:byte-buddy-agent:jar:1.12.19:test
[INFO]    |  \- org.objenesis:objenesis:jar:3.2:test
[INFO]    +- org.mockito:mockito-junit-jupiter:jar:4.5.1:test
[INFO]    +- org.skyscreamer:jsonassert:jar:1.5.1:test
[INFO]    |  \- com.vaadin.external.google:android-json:jar:0.0.20131108.vaadin1:test
[INFO]    +- org.springframework:spring-test:jar:5.3.24:test
[INFO]    \- org.xmlunit:xmlunit-core:jar:2.9.0:test
```

We can see here that `Spring Boot 2.7.6` relies on the `Spring Framework 5.3.24`

When we add Spring Security to the mix, we see that it relies on `Spring Security 5.7.5`

```
[INFO] --- maven-dependency-plugin:3.3.0:tree (default-cli) @ spring-boot-2.7.6 ---
[INFO] com.example:spring-boot-2.7.6:jar:0.0.1-SNAPSHOT
[INFO] +- org.springframework.boot:spring-boot-starter-security:jar:2.7.6:compile
[INFO] |  +- org.springframework.boot:spring-boot-starter:jar:2.7.6:compile
[INFO] |  |  +- org.springframework.boot:spring-boot:jar:2.7.6:compile
[INFO] |  |  +- org.springframework.boot:spring-boot-autoconfigure:jar:2.7.6:compile
[INFO] |  |  +- org.springframework.boot:spring-boot-starter-logging:jar:2.7.6:compile
[INFO] |  |  |  +- ch.qos.logback:logback-classic:jar:1.2.11:compile
[INFO] |  |  |  |  \- ch.qos.logback:logback-core:jar:1.2.11:compile
[INFO] |  |  |  +- org.apache.logging.log4j:log4j-to-slf4j:jar:2.17.2:compile
[INFO] |  |  |  |  \- org.apache.logging.log4j:log4j-api:jar:2.17.2:compile
[INFO] |  |  |  \- org.slf4j:jul-to-slf4j:jar:1.7.36:compile
[INFO] |  |  +- jakarta.annotation:jakarta.annotation-api:jar:1.3.5:compile
[INFO] |  |  \- org.yaml:snakeyaml:jar:1.30:compile
[INFO] |  +- org.springframework:spring-aop:jar:5.3.24:compile
[INFO] |  |  \- org.springframework:spring-beans:jar:5.3.24:compile
[INFO] |  +- org.springframework.security:spring-security-config:jar:5.7.5:compile
[INFO] |  |  +- org.springframework.security:spring-security-core:jar:5.7.5:compile
[INFO] |  |  |  \- org.springframework.security:spring-security-crypto:jar:5.7.5:compile
[INFO] |  |  \- org.springframework:spring-context:jar:5.3.24:compile
[INFO] |  \- org.springframework.security:spring-security-web:jar:5.7.5:compile
[INFO] |     +- org.springframework:spring-expression:jar:5.3.24:compile
[INFO] |     \- org.springframework:spring-web:jar:5.3.24:compile
[INFO] \- org.springframework.boot:spring-boot-starter-test:jar:2.7.6:test
[INFO]    +- org.springframework.boot:spring-boot-test:jar:2.7.6:test
[INFO]    +- org.springframework.boot:spring-boot-test-autoconfigure:jar:2.7.6:test
[INFO]    +- com.jayway.jsonpath:json-path:jar:2.7.0:test
[INFO]    |  +- net.minidev:json-smart:jar:2.4.8:test
[INFO]    |  |  \- net.minidev:accessors-smart:jar:2.4.8:test
[INFO]    |  |     \- org.ow2.asm:asm:jar:9.1:test
[INFO]    |  \- org.slf4j:slf4j-api:jar:1.7.36:compile
[INFO]    +- jakarta.xml.bind:jakarta.xml.bind-api:jar:2.3.3:test
[INFO]    |  \- jakarta.activation:jakarta.activation-api:jar:1.2.2:test
[INFO]    +- org.assertj:assertj-core:jar:3.22.0:test
[INFO]    +- org.hamcrest:hamcrest:jar:2.2:test
[INFO]    +- org.junit.jupiter:junit-jupiter:jar:5.8.2:test
[INFO]    |  +- org.junit.jupiter:junit-jupiter-api:jar:5.8.2:test
[INFO]    |  |  +- org.opentest4j:opentest4j:jar:1.2.0:test
[INFO]    |  |  +- org.junit.platform:junit-platform-commons:jar:1.8.2:test
[INFO]    |  |  \- org.apiguardian:apiguardian-api:jar:1.1.2:test
[INFO]    |  +- org.junit.jupiter:junit-jupiter-params:jar:5.8.2:test
[INFO]    |  \- org.junit.jupiter:junit-jupiter-engine:jar:5.8.2:test
[INFO]    |     \- org.junit.platform:junit-platform-engine:jar:1.8.2:test
[INFO]    +- org.mockito:mockito-core:jar:4.5.1:test
[INFO]    |  +- net.bytebuddy:byte-buddy:jar:1.12.19:test
[INFO]    |  +- net.bytebuddy:byte-buddy-agent:jar:1.12.19:test
[INFO]    |  \- org.objenesis:objenesis:jar:3.2:test
[INFO]    +- org.mockito:mockito-junit-jupiter:jar:4.5.1:test
[INFO]    +- org.skyscreamer:jsonassert:jar:1.5.1:test
[INFO]    |  \- com.vaadin.external.google:android-json:jar:0.0.20131108.vaadin1:test
[INFO]    +- org.springframework:spring-core:jar:5.3.24:compile
[INFO]    |  \- org.springframework:spring-jcl:jar:5.3.24:compile
[INFO]    +- org.springframework:spring-test:jar:5.3.24:test
[INFO]    \- org.xmlunit:xmlunit-core:jar:2.9.0:test
```


If we were to package this app we would see these JAR files  :

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
BOOT-INF/lib/slf4j-api-1.7.36.jar
BOOT-INF/lib/spring-core-5.3.24.jar
BOOT-INF/lib/spring-jcl-5.3.24.jar
BOOT-INF/lib/spring-boot-jarmode-layertools-2.7.6.jar
BOOT-INF/classpath.idx
BOOT-INF/layers.idx
```

So we already have 3 sets of versions that Spring Boot manages

```
Spring Boot     Spring Framework    Spring Security
2.7.6           5.3.24              5.7.5
2.7.1           5.3.21              5.7.2
```

The way Spring Boot does that is through its starter parents.

```
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.7.6</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
```

that in turn has the following parent

```
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-dependencies</artifactId>
    <version>2.7.6</version>
  </parent>
```

And this is where the magic happens. 
The `spring-boot-dependencies` contains all the versions of all the libraries that Spring depends on.
