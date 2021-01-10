### Random Port - Eureka
Criando portas aleatórias no 'application.properties' do projeto 'worker'

```
# Random port
server.port=${PORT:0}

eureka.instance.instance-id=${spring.application.name}:${spring.application.instance_id:${random.value}}
```

