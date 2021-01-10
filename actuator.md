### Actuator
Com o Actuator podemos dar refresh na aplicação e com isso pegar os valores atualizados de dados externos do projeto.

Foi incluído o Actuator no projeto 'hr-worker'.

Para baixar o 'Actuator' ao projeto é só acrescentar clicando com o botão direito no projeto, ir em 'Spring' > 'Add Starters' > Procurar e adicionar o 'Spring Boot Actuator'
nas opções de Spring Cloud.
Com isso o maven irá baixar as novas dependencias que será incluídas no pom.xml.

Na classe de aplicação incluir a anotação: '@RefreshScope'

No arquivo 'application.properties' do projeto 'hr-worker' inserir:
```
management.endpoints.web.exposure.include=*
```
