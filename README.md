# microservicos-transacoes
Aplicação distribuída para processamento de transações financeiras com RabbitMQ (AMQP). Lê transações de um CSV, processa com delay de 1s e identifica transações suspeitas (≥R$40k), notificando Polícia Federal e Receita Federal via Exchange fanout.
