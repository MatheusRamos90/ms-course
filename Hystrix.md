### Hystrix
Com o Hystrix podemos tratar timeouts, microserviços que estão fora do ar, retornar respostas alternativas caso haja erros.

Dentro do projeto de 'hr-payroll' do curso iremos adicionar:

Para baixar o Hystrix ao projeto é só acrescentar clicando com o botão direito no projeto, ir em 'Spring' > 'Add Starters' > Procurar e adicionar o 'Hystrix Maintenance'.
Com isso o maven irá baixar as novas dependencias que será incluídas no pom.xml.

Na classe de aplicação incluir a anotação: '@EnableCircuitBreaker'

Na classe controller 'PaymentResources' do projeto iremos adicionar uma anotação ao método público que faz a busca pelo pagamento do trabalhador.
A anotação é: '@HystrixCommand(fallbackMethod = "getPaymentAlternative")'
Essa anotação redireciona para um método alternativo que retorna alguma coisa no retorno da requisição HTTP.
O 'getPaymentAlternative' passado para o valor 'fallbackMethod' seria o nome do método alternativo.


No arquivo 'application.properties' do projeto 'hr-payroll' inserir:
```
hystrix.command.default.execution.isolation.thread.timeoutInMilliseconds=60000
ribbon.ConnectTimeout=10000
ribbon.ReadTimeout=20000
```