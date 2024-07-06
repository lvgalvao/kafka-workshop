# kafka-workshop

```mermaid
graph LR
    subgraph Producers
        Producer1["Producer 1"]
        Producer2["Producer 2"]
    end

    subgraph Kafka Cluster
        direction TB
        Zookeeper["Zookeeper"]
        Broker1["Broker 1"]
        Broker2["Broker 2"]
        Broker3["Broker 3"]
    end

    subgraph Consumers
        Consumer1["Consumer 1"]
        Consumer2["Consumer 2"]
        Consumer3["Consumer 3"]
    end

    Producer1 --> |"Send Messages"| Broker1
    Producer2 --> |"Send Messages"| Broker2

    Zookeeper --> |"Cluster Coordination"| Broker1
    Zookeeper --> |"Cluster Coordination"| Broker2
    Zookeeper --> |"Cluster Coordination"| Broker3

    Broker1 --> |"Consume Messages"| Consumer1
    Broker2 --> |"Consume Messages"| Consumer2
    Broker3 --> |"Consume Messages"| Consumer3
```

### Explicação do Diagrama:

1. **Producers**:
    
    * **Producer 1 e Producer 2**: Aplicações cliente que enviam mensagens para os brokers do cluster Kafka.
2. **Kafka Cluster**:
    
    * **Zookeeper**: Coordena e gerencia o estado do cluster Kafka, colocado acima dos brokers.
    * **Brokers (Broker 1, Broker 2, Broker 3)**: Servidores Kafka que armazenam e gerenciam os dados. Eles recebem mensagens dos producers e as encaminham para os consumers.
3. **Consumers**:
    
    * **Consumer 1, Consumer 2, Consumer 3**: Aplicações cliente que consomem mensagens dos brokers.

### Fluxo de Dados:

* **Producers** enviam mensagens para os **Brokers**.
* **Brokers** armazenam as mensagens e se comunicam com o **Zookeeper** para coordenação.
* **Consumers** consomem mensagens dos **Brokers**.

Este diagrama organizado da esquerda para a direita e com o Zookeeper acima dos brokers dentro do Kafka Cluster ilustra claramente o fluxo de dados e a coordenação dentro do sistema.