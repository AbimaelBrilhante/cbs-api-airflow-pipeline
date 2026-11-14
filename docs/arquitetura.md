# Arquitetura técnica — CBS API Data Pipeline

[Voltar à apresentação](../README.md)

## Objetivo de engenharia

Organizar a obtenção de dados de apuração CBS por serviços externos, com etapas observáveis de integração, acompanhamento e preparação de dados para consumo analítico.

O projeto considera três necessidades centrais: **continuidade de processamento**, **integridade do histórico recebido** e **visibilidade operacional**.

## Visão dos componentes

```mermaid
flowchart TB
    subgraph Origem["Origem"]
      API["Serviços externos de apuração CBS"]
    end
    subgraph Processamento["Plataforma de engenharia de dados"]
      AIR["Orquestração e monitoramento<br/>Apache Airflow"]
      INT["Integração de serviços<br/>Python / REST"]
      EST["Controle persistente<br/>de processamento"]
      RAW["Armazenamento de dados de origem"]
      STD["Preparação e consolidação"]
      AIR --> INT
      INT <--> EST
      INT --> RAW
      RAW --> STD
    end
    API <--> INT
    STD --> OUT["Saídas estruturadas para análise"]
```

## Responsabilidades por camada

| Camada | Objetivo | Considerações de engenharia |
| --- | --- | --- |
| **Origem externa** | Disponibilizar informações de apuração | Dependência de disponibilidade e autorização do serviço |
| **Integração** | Interagir com APIs e receber respostas | Validação de respostas e isolamento da integração |
| **Orquestração** | Coordenar etapas e acompanhar execuções | Observabilidade, dependências e diagnóstico |
| **Controle de estado** | Registrar o progresso dos processos | Recuperação e consistência do acompanhamento |
| **Persistência de origem** | Preservar dados recebidos | Rastreabilidade e conferência posterior |
| **Preparação de dados** | Organizar informações para análise | Padronização, consistência e histórico |
| **Consumo analítico** | Disponibilizar extratos estruturados | Integração futura com plataformas analíticas |

## Princípios de qualidade

**Resiliência.** Interrupções e resultados não conclusivos precisam ser distinguíveis de processamento concluído, com visibilidade para análise operacional.

**Integridade.** Os dados recebidos devem ser preservados de modo a viabilizar verificações e rastreabilidade entre origem e saída estruturada.

**Separação de responsabilidades.** Integração, orquestração, armazenamento e transformação representam preocupações diferentes e podem evoluir com menor acoplamento.

**Testabilidade.** Os comportamentos críticos podem ser avaliados com cenários sintéticos, sem depender de credenciais ou dados fiscais reais durante os testes.

## Sobre a versão em produção

A versão utilizada em produção é mantida em um repositório privado por conter dados sensíveis.
