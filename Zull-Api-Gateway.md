### Zuul (API Gateway)

- Roteando os microserviços com uma API Gateway usando o Zuul, e o Eureka Client.

Para isso foi criado um projeto chamado 'hr-api-gateway-zuul'
Na classe de aplicação incluir a anotação: '@EnableEurekaClient' e '@EnableZuulProxy'

No arquivo 'application.properties' do projeto 'hr-api-gateway-zuul' inserir:
```
spring.application.name=hr-api-gateway-zuul

# Default port for Zuul (always will be this port). Not have random port.
server.port=8765

# Eureka Server
eureka.client.service-url.defaultZone=http://localhost:8761/eureka

# Configuration Hystrix
hystrix.command.default.execution.isolation.thread.timeoutInMilliseconds=60000
ribbon.ConnectTimeout=10000
ribbon.ReadTimeout=20000

# Routes microservices configuration (gateway api)
zuul.routes.worker.service-id=hr-worker
zuul.routes.worker.path=/hr-worker/**

zuul.routes.payroll.service-id=hr-payroll
zuul.routes.payroll.path=/hr-payroll/**
```

A porta para este projeto que servirá como roteador de rotas não deve ser randomica, e sim uma já pre-estabelecida. No exemplo, é a 8765.
É necessário registrar neste arquivo properties as rotas que será roteadas a partir do nome do microserviço.
É necessário registrar também a rota HTTP da API Gateway. Dessa forma será feito um roteamento do projeto web 'hr-api-gateway-zuul' para 
os outros projetos.

Detalhe: o Hystrix foi adicionado também para fazer tratamento de timeouts caso aconteça.