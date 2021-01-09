## FEIGN
O feign é um componente do Spring Cloud que é uma forma alternativa de comunicar um projeto com outro.
Ele tem as outras ferramentas do Spring Cloud incluídas nele (essa é a maior vantagem dele).

Para adicionar o Feign é necessário acrescentar clicar com o botão direito no projeto, ir em 'Spring' > 'Add Starters' > Procurar e adicionar o 'OpenFeign'.
Com isso o maven irá baixar as novas dependencias que será incluídas no pom.xml.

Na classe principal da aplicação (starter), colocar a anotação '@EnableFeignClients'.

Criar uma interface que chama outro serviço/projeto.
Anotações especiais: @FeignClient(name = "hr-worker", url = "localhost:8001", path = "/workers")