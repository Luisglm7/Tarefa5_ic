# Arquitetura da Solução e Uso da Nuvem

## 1. Componentes da Solução
A proposta técnica consiste em um ecossistema integrado para monitoramento industrial, composto por:
- **IoT / Sensores:** Captura de pulsos elétricos e estados de máquina via sensores conectados.
- **Back-end:** Processamento de dados via AWS IoT Core e funções Serverless (AWS Lambda).
- **Banco de Dados:** Armazenamento em nuvem utilizando Amazon DynamoDB.
- **Dashboard:** Interface web desenvolvida para exibição de indicadores de eficiência (OEE) em tempo real.
- **Inteligência Artificial:** Uso de modelos preditivos para alertas de baixa produtividade (Amazon SageMaker).

## 2. Infraestrutura (Cloud AWS)
A solução será executada na nuvem da **AWS**, aproveitando a escalabilidade e o baixo custo de serviços serverless. A captura será feita via protocolo MQTT, garantindo baixa latência no envio das informações da fábrica para o painel de controle.

## 3. Diagrama da Arquitetura (Mermaid)

```mermaid
graph LR
    A[Máquina / Sensores] -->|Telemetria MQTT| B(AWS IoT Core)
    B --> C{AWS Lambda}
    C --> D[(DynamoDB)]
    C --> E[Amazon SNS - Alertas]
    D --> F[Dashboard de Produtividade]
    F --> G[Gestor de Produção]