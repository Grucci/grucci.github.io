---
title: Fundamentos do Terraform (parte 1)
slug: fundamentos-do-terraform-parte-1
author: grucci
date: 2023-10-31
summary: "Conheça os fundamentos do Terraform: sua arquitetura, o papel dos providers e as diferenças entre backends locais e remotos, além da importância do state file para acompanhar recursos, dependências e alterações na infraestrutura."
img_path: images/
tags: [iac, terraform, fundamentals]
emoji: "🏗️"
featured: false
---

## O que é Terraform?

Terraform é uma ferramenta de Infraestrutura como Código (IaC), criada pela HashiCorp, que permite a criação, o gerenciamento e o provisionamento automatizados e consistentes de recursos de infraestrutura na nuvem e on-premises.

É uma ferramenta de programação declarativa que utiliza uma linguagem de alto nível chamada HCL (HashiCorp Configuration Language) e pode gerenciar tanto componentes de baixo nível (ex:. armazenamento) quanto componentes de alto nível (ex:. SaaS).

## Principais recursos do Terraform

* Não é necessário instalar nenhum aplicativo além do binário do Terraform.
* Os arquivos do Terraform usam a extensão .tf.
* Os plugins são baixados após a inicialização do Terraform para a pasta .terraform, de acordo com as configurações.
* Armazena o estado do provisionamento da infraestrutura, e quaisquer modificações são registradas ao aplicar o código do Terraform.

## Composição da arquitetura do Terraform

O Terraform Core analisa as configurações e estabelece dependências entre os recursos.

Os Terraform Providers atuam como intermediários entre o Terraform Core e as APIs correspondentes.

## Componentes do Terraform

### *Backend*

O backend é uma configuração do Terraform que especifica onde o state file será armazenado.

Há várias maneiras de armazenar o state file, e a escolha depende das necessidades e dos requisitos do projeto.

Local (padrão): o estado é armazenado localmente no sistema de arquivos do computador em que o Terraform está sendo executado. No entanto, essa opção não é recomendada para ambientes de produção ou colaborativos, pois pode causar problemas de sincronização e segurança.

Remoto: o estado pode ser armazenado remotamente em um backend, como Amazon S3, Azure Storage Account, Google Cloud Storage, entre outros. Essa opção é altamente recomendada para ambientes de produção e equipes colaborativas, pois oferece benefícios como controle de acesso mais granular, possibilidade de trabalho colaborativo e maior segurança.

Exemplo de configuração de backend:

```terraform
1 terraform {
2   backend "s3" {
3     bucket         = "s3-bucket-name"
4     key            = "path/to/terraform.tfstate"
5     region         = "region-aws"
6     encrypt        = true
7   }
8 }
```

```terraform
1 terraform {
2   backend "azurerm" {
3     resource_group_name  = "rg-terraform-state"
4     storage_account_name = "mystorageaccountname"
5     container_name       = "tfstate"
6     key                  = "prod.terraform.tfstate"
7   }
8 }
```

### *State File*

O estado do Terraform é um arquivo que acompanha informações sobre os recursos provisionados, suas configurações e as dependências entre eles. Esse arquivo é essencial para que o Terraform compreenda o estado atual da infraestrutura e determine quais alterações são necessárias para alcançar o estado desejado.

O state file tem várias finalidades no Terraform:

Rastreamento de recursos: o state file mantém um registro de todos os recursos provisionados pelo Terraform. Ele armazena identificadores exclusivos, configurações e metadados associados a cada recurso.

Controle de dependências: o state file registra as dependências entre os recursos. Isso é essencial para garantir que os recursos sejam criados ou modificados na ordem correta, evitando problemas de dependência.

Concorrência e bloqueio: o state file é usado para coordenar operações simultâneas de várias instâncias do Terraform. Ele fornece um mecanismo de bloqueio para garantir que apenas uma instância do Terraform por vez possa modificar o estado.

É essencial gerenciar o estado corretamente para evitar conflitos e garantir a integridade da infraestrutura gerenciada pelo Terraform.

Exemplo de State File:

![statefile-example](state_file.png)

### *Provider*

Os Terraform Providers são plugins usados para interagir e se conectar a um provedor de serviços ou recursos, como provedores de nuvem, armazenamento, rede, entre outros. Eles funcionam como pontes entre o Terraform Core e a API do serviço ou recurso a ser provisionado ou gerenciado. Cada provider é responsável por traduzir as instruções da configuração do Terraform em chamadas apropriadas para a API do provedor subjacente.

Alguns providers exigem configurações antes de serem usados (credenciais, região da nuvem, URL do endpoint etc.).

![terraformcore-provider](terraformcore-api.png)

Por exemplo, se você estiver usando o Terraform para provisionar recursos na Amazon Web Services (AWS), precisará do provider da AWS. Da mesma forma, se estiver trabalhando com o Microsoft Azure, precisará do provider do Azure. Cada provider tem seus próprios recursos e parâmetros, que podem ser configurados no arquivo de configuração do Terraform.

```terraform
1  provider “aws” {
2    region = “us-east-1”
3  }
```

```terraform
1  provider "azurerm" {
2    features {}
3  }
```

A estrutura modular do Terraform permite que os usuários escolham e incorporem providers específicos conforme necessário para atender aos requisitos da infraestrutura que estão criando. Essa abordagem oferece ampla flexibilidade e suporte para diferentes ambientes e serviços de infraestrutura.

![provider](providers.png)