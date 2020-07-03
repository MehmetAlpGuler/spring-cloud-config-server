### Spring Cloud Config Server

- http://localhost:8888/limits-service/default
- http://localhost:8888/limits-service/dev
- http://localhost:8888/limits-service/qa


- http://localhost:8080/limits


![](images/spring-cloud-config-server-sheme.png)


## Spring Cloud Config Server
![](images/spring-cloud-config-server.png)

pom.xml
```json
<dependencies>
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-config-server</artifactId>
    </dependency>

    ***
</dependencies>
```

application.properties
```json
spring.application.name=spring-cloud-config-server
server.port=8888
spring.cloud.config.server.git.uri=https://github.com/MehmetAlpGuler/spring-cloud-config-server-properties.git
```
SpringCloudConfigServerApplication.java
```json
@EnableConfigServer //just this annotation added for spring cloud config server
@SpringBootApplication
public class SpringCloudConfigServerApplication {

	public static void main(String[] args) {
		SpringApplication.run(SpringCloudConfigServerApplication.class, args);
	}

}
```


## Spring Cloud Config Client Microservice
###limits-service
![](images/spring-cloud-config-server-client.png)

pom.xml
```json
<dependencies>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-config</artifactId>
    </dependency>

    ***
</dependencies>
```

bootstrap.properties
```json
spring.application.name=limits-service
spring.cloud.config.uri=http://localhost:8888
spring.profiles.active=dev
management.security.enabled=false
```