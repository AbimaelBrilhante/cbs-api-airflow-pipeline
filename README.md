# CBS API Data Pipeline
### Engenharia de dados para a Reforma Tributária Brasileira

**Portfólio técnico | Python · Apache Airflow · Docker · REST APIs · ETL**

[English version](README.en.md) · [Arquitetura técnica](docs/arquitetura.md)

> **Apresentação técnica do projeto.** Este repositório público documenta a arquitetura, o escopo e as competências de engenharia envolvidas. A implementação operacional e o código-fonte permanecem em ambiente privado.

## Visão geral

O **CBS API Data Pipeline** é uma solução de engenharia de dados voltada à integração com serviços de apuração da Contribuição sobre Bens e Serviços (CBS), no contexto da Reforma Tributária brasileira.

O desafio é transformar a obtenção de dados fiscais por APIs assíncronas em um processo **rastreável, recuperável e preparado para análise**, considerando dependências externas, diferentes estados de processamento e a necessidade de preservar a integridade das informações recebidas.

Este portfólio demonstra a arquitetura da solução, sem disponibilizar rotinas internas, credenciais, dados fiscais ou artefatos executáveis.

## Arquitetura em alto nível

```mermaid
flowchart LR
    A["APIs de apuração CBS"] --> B["Camada de integração"]
    O["Apache Airflow<br/>Orquestração e observabilidade"] --> B
    B <--> S[("Controle de processamento")]
    B --> C[("Dados recebidos<br/>JSON")]
    C --> D["Padronização e consolidação"]
    D --> E[("Dados estruturados<br/>para análise")]
```

A representação acima é **conceitual**: descreve as responsabilidades dos componentes, não a implementação interna nem o detalhamento das regras técnicas.

## Competências demonstradas

| Pilar | Aplicação no projeto |
| --- | --- |
| **Integração de APIs** | Coleta de dados em serviços com processamento assíncrono |
| **Orquestração** | Organização e acompanhamento dos fluxos com Apache Airflow |
| **Resiliência** | Continuidade de processamento e tratamento controlado de falhas |
| **Engenharia de dados** | Preservação do dado de origem e preparação de saídas estruturadas |
| **Rastreabilidade** | Identificação de etapas, resultados e pontos de atenção do processamento |
| **Ambiente reproduzível** | Separação de componentes e dependências com Docker |
| **Qualidade** | Validação por testes com cenários e dados simulados |

## Tecnologias

**Python** · **Apache Airflow** · **Docker / Docker Compose** · **PostgreSQL** · **SQLite** · **pandas** · **HTTP/REST** · **JSON / CSV** · **GitHub Actions**

As tecnologias estão listadas para apresentar o repertório técnico empregado na versão de demonstração. Detalhes de configuração e integração não fazem parte desta publicação.

## Escopo e evolução

A solução contempla a arquitetura de coleta, acompanhamento e preparação de informações relacionadas à apuração CBS, incluindo cenários de débitos e créditos. A expansão de integrações e a evolução operacional são tratadas em ambiente privado.

Este repositório **não oferece um serviço público, instalação executável ou acesso aos dados coletados**.

## Documentação

- [Arquitetura e responsabilidades dos componentes](docs/arquitetura.md)
- [English overview](README.en.md)

## Sobre

Projeto de portfólio de **Abimael Brilhante**, com foco em engenharia de dados, integração de sistemas, automação e domínio de processos fiscais.

**Perfil técnico:** [GitHub — AbimaelBrilhante](https://github.com/AbimaelBrilhante).

*Projeto independente, sem vínculo oficial com a Receita Federal ou o SERPRO. As informações apresentadas são de caráter técnico e demonstrativo.*

© 2026 Abimael Brilhante. Todos os direitos reservados. A publicação desta documentação não autoriza a reprodução ou exploração comercial da implementação privada.
