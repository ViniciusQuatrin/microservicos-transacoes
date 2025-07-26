# Processamento Distribuído de Transações Financeiras com RabbitMQ

Aplicação distribuída para processar transações financeiras usando RabbitMQ e o protocolo AMQP. O sistema lê um CSV, publica cada linha como mensagem na fila `transacoes.financeiras`, processa com atraso de 1s por transação e, para valores ≥ R$ 40.000, publica em um exchange fanout que encaminha simultaneamente para `policia.federal` e `receita.federal`.

## Funcionalidades

- Leitura de arquivo CSV (`transacoes.csv`).
- Produtor envia cada registro para a fila `transacoes.financeiras`.
- Consumidor processa cada mensagem com delay programado de 1 segundo.
- Transações ≥ R$ 40.000 são marcadas como suspeitas e enviadas ao exchange fanout `transacoes.suspeitas`.
- Exchange fanout encaminha para as filas `policia.federal` e `receita.federal`.

## Tecnologias

- Java 17 (ou versão usada)
- Spring Boot (spring-boot-starter-amqp, web, etc.)
- Spring AMQP / RabbitTemplate
- Maven
- Docker / Docker Compose (para o RabbitMQ)

## Como executar

1. Suba um RabbitMQ localmente ou via Docker.
2. Configure filas e exchanges conforme o código.
3. Rode o Produtor para publicar as mensagens.
4. Rode os Consumidores para processar e encaminhar notificações.
