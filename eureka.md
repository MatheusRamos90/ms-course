### Eureka Server

Criar o projeto de microserviços do eureka-server.

Requisitos para versões do Java 11:
- Baixar o JAXB Runtime

```
<!-- https://mvnrepository.com/artifact/org.glassfish.jaxb/jaxb-runtime -->
<dependency>
    <groupId>org.glassfish.jaxb</groupId>
    <artifactId>jaxb-runtime</artifactId>
</dependency>
```

Na classe de aplicação incluir a anotação: '@EnableEurekaServer'

No arquivo 'application.properties' do projeto 'eureka server' inserir:
```
spring.application.name=hr-eureka-server
server.port=8761

eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```

Nos projetos 'workers' e 'payroll' que serão utilizado pelo server do eureka temos que incluir nas
dependências o 'Eureka Discovery Client'.

Para adicionar o 'Eureka Discovery Client' é necessário acrescentar clicando com o botão direito no projeto, ir em 'Spring' > 'Add Starters' > Procurar e adicionar o 'Eureka Discovery Client'.
Com isso o maven irá baixar as novas dependencias que será incluídas no pom.xml.

Logo depois adicionar no arquivo 'application.properties' do 'worker' e 'payroll':

```
# Eureka Server
eureka.client.service-url.defaultZone=http://localhost:8761/eureka`
```

Na classe de aplicação do projeto 'worker' e do 'payroll' incluir a anotação: '@EnableEurekaClient'

### Observação
- Com o que foi feito acima nós conseguimos identificar o servidor eureka, e registramos nele os nossos microserviços