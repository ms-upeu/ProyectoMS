# ProyectoMS
Arquitectura base de microservicios con Spring Boot


Ejecutar:

Eureka registry-server http://localhost:8090/

	server:
	  port: 8090
	eureka:
	  instance:
	    hostname: localhost
	  client:
	    registerWithEureka: false
	    fetchRegistry: false
	    serviceUrl:
	      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/

config-server http://localhost:7070

	server:
	  port: 7070
	spring:
	  application:
	    name: config-server
	  cloud:
	    config:
	      server:
	        git:
	          uri: https://github.com/ms-upeu/ProyectoMS.git
	          searchPaths: config-data
	          #username:
	          #password:
	          default-label: main
	  security:
	    user:
	      name: root
	      password: 123456


ms-catalogo-service http://localhost:8081/doc/swagger-ui/index.html

	server:
	  port: 8081
	springdoc:
	  api-docs:
	    enabled: true
	  swagger-ui:
	    enabled: true
	    path: /doc/swagger-ui.html
	spring:
	  jpa:
	    hibernate.ddl-auto: update
	    generate-ddl: true
	    show-sql: true
	  datasource:
	    driverClassName: com.mysql.cj.jdbc.Driver
	    url: jdbc:mysql://localhost:3306/ms_catalogo
	    username: root
	    password:
	eureka:
	  client:
	    serviceUrl:
	      defaultZone: http://localhost:8090/eureka
	  instance:
	    hostname: localhost




## Comandos iniciales de git

Actualizar rama principal:

	git add .
	git commit -m "Registro y descubrimiento Eureka"
	git push origin main

Crea a partir de la rama actual:

	git branch 04-registry-server


Para subir al remoto:

	git push origin 04-registry-server


