# ProyectoMS
Arquitectura base de microservicios con Spring Boot


Ejecutar:

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

	spring:
	  application:
	    name: ms-catalogo-service
	  profiles:
	    active: development
	  config:
	    import: optional:configserver:http://root:123456@localhost:7070



## Comandos iniciales de git

Actualizar rama principal:

	git add .
	git commit -m "Configuración centralizada OK"
	git push origin main

Crea a partir de la rama actual:

	git branch 03-config-server


Para subir al remoto:

	git push origin 03-config-server


