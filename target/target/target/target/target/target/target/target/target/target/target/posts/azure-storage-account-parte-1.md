---
title: Azure Storage Account: fundamentos, arquitetura e boas práticas (parte 1)
slug: azure-storage-account-parte-1
author: grucci
date: 2023-11-01
summary: "Um guia para entender os serviços de armazenamento da Azure e suas aplicações em ambientes corporativos."
img_path: images/
tags: [storage, account, armazenamento, azure, fundamentals]
emoji: "💾"
featured: false
---aqui mais um teste de PR

Depois de algumas mudanças no trabalho, comecei a fazer parte do time responsável pelos produtos relacionados a Storage, o que me levou a novos desafios e oportunidadesde aprofundar meus conhecimentos sobre os serviçoes de armazenamento disponíveis nos diversos Cloud Providers.

Com isso surgiu a necessidade de entender melhor não apenas os produtos com os quais passaria a trabalhar, mas também suas arquiteturas, caractéristicas, possibilidades de utilização e os principais pontos de atençãoem ambientes corporativos.

Um dos primeiros assuntos que estou me dedicando a estudar é o *Azure Storage Account*, principalmente pela quantidade de demandas relacionadas a esse serviço.

## O que é um Storage Account?

Uma Azure Storage Account é um recurso de infraestrutura responsável por disponibilizar e gerenciar serviços de armazenamento de dados dentro do Microsoft Azure.

Ele funciona como uma estrutura lógica que reúne diferentes serviços de armazenamento, permitindo que aplicações, usuários e outros recursos de nuvem armazenem e acessem informações de maneira escalável e segura.

É possível trabalhar com diferentes tipos de dadaos e necessidades, como:

* Arquivos e documentos
* Imagens e Vídeos
* Banckups e Arquivos históricos
* Logs de aplicações e Infraestrutura
* Mensagens utilizadas na comunicação entre sistemas
* Dadsos estruturados e não estruturados
* Compartilhamentos de arquivos utilizados por aplicações e servidores

Uma característica importante é que a Storage Account não representa simplesmente um disco virtual ou um espaço de armarzenamento. Ele disponibiliza diferentes serviços, cada um desenvolvido para atender padrões de utilização e necessidades de arquitetura diferentes.

Principais serviços:

* Blob Storage: armazenamento de objetos não estruturados
* Azure Files: compartilhamento de arquivos
* Queue Storage: armazenamento de mensagens para processamento assíncrono
* Table Storage: armazenamento NoSQL de dados

Cada serviço possui características específicas de desempenho, acesso, escalabilidade e custo, que devem ser consideradas durante o planejamento da arquitetura.

## Qual problema a Storage Account resolve?

## Como funciona o armazenamento em nuvem?

## Quais são as principais características?

## Diferença entre armazenamento tradicional (on-premises) e armazenamento em nuvem

## Quais cenários justificam sua utilização?

---
## Referências

- [Visão geral das contas de armazenamento](https://learn.microsoft.com/pt-br/azure/storage/common/storage-account-overview)
- [O que é uma storage account?](https://www.linkedin.com/pulse/o-que-%C3%A9-uma-storage-account-leandro-chiesa/)
- [Azure Storage - Explorando os Diferentes Tipos de Armazenamento](https://medium.com/@habbema/azure-storage-0226b2db1daf)
- [Diferenças entre Blob Storage e Azure Files](https://unicast.com.br/posts/diferencas-entre-blob-storage-e-azure-files/)
- [Azure Storage Accounts](https://www.nathanpinotti.com.br/azure-storage-account/)