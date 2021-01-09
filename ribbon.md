### Ribbon (balanceador de carga)
É possível levantar a mesma instância de um projeto, quando há uma chamada para outro projeto com mais de uma instância levantada... vai haver ali
um balanceamento de carga, ou seja, algumas requisições vão pegar dados de uma instância e outras requisições de outras instâncias.

Para adicionar o Ribbon é necessário acrescentar clicando com o botão direito no projeto, ir em 'Spring' > 'Add Starters' > Procurar e adicionar o 'Ribbon'.
Com isso o maven irá baixar as novas dependencias que será incluídas no pom.xml.

- Tudo o que será feito abaixo será feito de forma MANUAL por enquanto

Na classe principal da aplicação (starter), colocar a anotação '@RibbonClient(name = "NOME_DO_MICROSERVICO")'.

No arquivo 'application.properties' do 'src/main/resources'
hr-worker.ribbon.listOfServers=localhost:8001,localhost:8002 // exemplo

Para checar se o balanceador está funcionando é só adicionar ao log do console a porta da environment.
Através da interface 'private Environment env'.
Adicionar no método do controlador 'logger.info("PORT = " + env.getProperty("local.server.port"));'. 
Com isso se for feito duas requisições será balanceado as cargas.