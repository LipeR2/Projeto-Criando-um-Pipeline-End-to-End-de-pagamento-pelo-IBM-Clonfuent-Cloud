# Projeto: Criando um Pipeline End-to-End (de pagamento) pelo IBM Clonfuent Cloud.



## 📚 Descrição:
>***O repositório é um Lab. (laboratório) com intenção de aplicar conceitos de pipeline em tempo real em Cloud. Em específico nesse cenário o uso do SGBD (Sistema Gerenciados de Banco de Dados) PostgreSQL, ingestão por CDC, processados pelo Apache Flink SQL em fluxo contínuo, de um data streaming. Nesse Pipeline de pagamento tem as seguinte função, praticar banco de dados até o alerta de fraude na nuvem.***

## ✅ Tópicos de Construção (camadas):
- *Fundação;*
- *Contrato de dados;*
- *Ingestão (CDC);*
- *Processamento (Flink SQL);*
- *Custo total de teardown.*

## 💻 Resumos: 
```
PostegreSQL + Apache Flink SQL + IBM Confluent Cloud
```

| **Temas** | **Resumos** |
|-------|---------|
| **Fundação** | Criar o ambiente e o cluster, com uma identidade para quem escreve e outra para quem lê. |
| **Contrato** | Registrar o formato das mensagens no Schema Registry e testar se ele aguenta uma mudança de campo. |
| **Ingestão** | Ligar o conector de CDC ao Postgres e ver o insert, o update e o delete chegando como evento. |
| **Processamento** | No Flink SQL, enriquecer a transação com os dados da conta e escrever a regra de fraude: três transações no mesmo cartão em 60 segundos viram um alerta. |
| **Operação** | Olhar as métricas, o acesso e o custo do que você subiu. |

## Framework dos Processos:

```mermaid
flowchart TD
    A[Pipeline:]
    B[Neon ``PostgreSQL``] --> C[CDC Debezium]
    C[CDC Debezium] --> D[tópicos Avro]
    D[tópicos Avro] --> E[Flink SQL ``enriquecimento + fraude``]
    E[Flink SQL ``enriquecimento + fraude``] --> F[consumo. Reproduzível com ``./setup.sh`` (pré-requisito: ``.env preenchido`` a partir do
``.env.example`` )]   
```

## 📈🗂️🧑🏻‍💻 Atividades Relacionadas ao Lab.:
- Teardown, um conceito de processo analítico que desmontar ou desconstruir um sistema;
- Entre outros.

## 🔍 Referências:
- [DIO - IBM Confluent Cloud]()
