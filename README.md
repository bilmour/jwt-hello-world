# Spring Bot - JWT
Spring Boot Application that makes use of JWT authentication for securing an exposed REST API. In this example we will be making use of hard coded user values for User Authentication

-> Develop a Spring Boot Application to expose a Simple REST GET API with mapping /hello.

-> Configure Spring Security for JWT. Expose REST POST API with mapping /authenticate using which User will get a valid JSON Web Token. And then allow the user access to the api /hello only if it has a valid token

https://start.spring.io/


A saber : 

Configurar tu applicacion STATELESS En el WebSecurityConfig :


    // make sure we use stateless session; session won't be used to
    // store user's state. 
                  exceptionHandling().authenticationEntryPoint(jwtAuthenticationEntryPoint).and().sessionManagement()
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS);



Problemas encontrados : 

## 1) application.properties 

### spring boot 2.6.4. : circular dependency is prohibited by default
### spring.main.allow-circular-references: true

Esta propiedad corrige el problema de dependencia circular que aparece con la version 


## 2) java 11

### java.lang.ClassNotFoundException: javax.xml.bind.DatatypeConverter en java 11 al generar el token 
Al generar el token, en el momento de firmarlo ha aparecido este error asociado a la java 11
<!-- Runtime, com.sun.xml.bind module -->
<!-- java.lang.ClassNotFoundException: javax.xml.bind.DatatypeConverter en java 11 al generar el token -->

    <dependency>
			  <groupId>org.glassfish.jaxb</groupId>
			  <artifactId>jaxb-runtime</artifactId>
			  <version>3.0.2</version>
     </dependency>





