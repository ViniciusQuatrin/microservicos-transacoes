📊 Processamento Distribuído de Transações Financeiras com RabbitMQ 
Este projeto implementa uma aplicação distribuída para processamento de dados de transações financeiras utilizando RabbitMQe o protocolo AMQP (Advanced Message Queuing Protocol).
O sistema é composto por Produtores, Consumidores e Filas, conforme descrito na imagem acima, e simula um ambiente de troca de mensagens assíncronas.

⚙️ Funcionalidades 

✅ Leitura de transações financeiras via CSV  Um Produtor processa um arquivo transacoes.csv (1000 transações). Cada linha do arquivo é convertida em uma mensagem enviada para a fila transacoes.financeiras. 

✅ Processamento das transações  Um Consumidor lê as mensagens da fila transacoes.financeiras.Cada transação é processada com um delay programado de 1 segundo por transação, simulando um fluxo real de processamento. 

✅ Detecção e notificação de transações suspeitas  Transações iguais ou superiores a R$ 40.000 são consideradas suspeitas.  O Consumidor envia essas transações para um Exchange do tipo fanout (transacoes.suspeitas). O Exchange envia mensagens simultaneamente para as filas:  policia.federal  receita.federal  

✅ Integração com múltiplos consumidores  A Polícia Federal e a Receita Federal recebem as mensagens em paralelo, cada uma processando conforme suas regras. 

🛠 Tecnologias Utilizadas Linguagem: (SpringBoot, Java)  
Mensageria: RabbitMQ + AMQP 
Formato de entrada: CSV  

🚀 Como Executar 
Inicie um servidor RabbitMQ local ou via Docker.  
Configure as filas e o exchange conforme descrito no código.  
Execute o Produtor para enviar as transações. 
Execute o(s) Consumidor(es) para processar as mensagens.
