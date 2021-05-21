# KafkaHandsOn
Construção de uma aplicação simples para exemplificar a implementação de um  __producer__ e um __consumer__ na plataforma .NET, explorando opções de performance e segurança.

Para realizar os testes, utilizaremos o kafka localmente através do docker. :space_invader:

Imagem disponibilizada nos tutoriais da confluent aqui -> [Kafka tutorials confluent.](https://kafka-tutorials.confluent.io/kafka-console-consumer-producer-basics/kafka.html)
```
---
version: '2'

services:
  zookeeper:
    image: confluentinc/cp-zookeeper:6.1.0
    hostname: zookeeper
    container_name: zookeeper
    ports:
      - "2181:2181"
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000

  broker:
    image: confluentinc/cp-kafka:6.1.0
    hostname: broker
    container_name: broker
    depends_on:
      - zookeeper
    ports:
      - "29092:29092"
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: 'zookeeper:2181'
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: PLAINTEXT:PLAINTEXT,PLAINTEXT_HOST:PLAINTEXT
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://broker:9092,PLAINTEXT_HOST://localhost:29092
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
      KAFKA_GROUP_INITIAL_REBALANCE_DELAY_MS: 0
```
:speech_balloon:(Salve o arquivo e execute no mesmo diretório o comando _docker-compose up -d_)

Fica também a sugestão de instalar alguma ferramenta para visualizar as informações:
[Conduktor](https://www.conduktor.io/) -> Utilizaremos essa na apresentação
[Kafka Magic](https://www.kafkamagic.com/)
[Kafka Tool](https://www.kafkatool.com/)
