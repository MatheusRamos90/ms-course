### Config Server
Será criado um projeto chamado 'hr-config-server' que usará o Config Server do Spring Cloud.

Dentro do projeto de 'hr-config-server' do curso iremos adicionar:

Para baixar o 'Config Server' ao projeto é só acrescentar clicando com o botão direito no projeto, ir em 'Spring' > 'Add Starters' > Procurar e adicionar o 'Config Server'
nas opções de Spring Cloud.
Com isso o maven irá baixar as novas dependencias que será incluídas no pom.xml.

Na classe de aplicação incluir a anotação: '@EnableConfigServer'

No arquivo 'application.properties' do projeto 'hr-config-server' inserir:
```
spring.application.name=hr-config-server
# Configuration for branch 'main' (Github)
spring.cloud.config.server.git.default-label=main
server.port=8888

# Repository (Github)
spring.cloud.config.server.git.uri=https://github.com/MatheusRamos90/ms-course-configs
```

Foi criado um repositório no Github com dois arquivos para leitura dos dados de configuração do microserviço.

No projeto de microserviço 'hr-worker' foi alterado o arquivo 'application.properties'
```
spring.application.name=hr-worker
spring.cloud.config.uri=http://localhost:8888

spring.profiles.active=test
```