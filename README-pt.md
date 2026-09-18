
# Foster

<p align="center">
  <a href="https://fosterstores.onrender.com">
    <img src="public/images/laptopFoster.png" alt="Prévia da aplicação Foster" width="650">
  </a>
</p>

<p align="center">
  <a href="README-pt.md">Português</a>
  ·
  <a href="README.md">English</a>
</p>

<p align="center">
  Aplicação web para cadastro, organização e localização de estabelecimentos comerciais.
</p>

## Sobre o projeto

O **Foster** é uma aplicação web voltada ao cadastro e à visualização de estabelecimentos comerciais.

A aplicação atual oferece um fluxo básico completo para:

- cadastrar um estabelecimento;
- armazenar suas informações em um banco SQLite;
- listar os estabelecimentos cadastrados;
- exibir os estabelecimentos em um mapa interativo;
- visualizar os detalhes de um estabelecimento;
- disponibilizar localização, horário de atendimento, contato, imagens e instruções.

O projeto começou como uma aplicação acadêmica e experimental e evoluiu para um sistema web funcional, executado no servidor, utilizando **Node.js, Express, Handlebars e SQLite**.

> **Escopo atual:** o Foster é um protótipo de diretório e gestão de estabelecimentos. **Não é um ERP completo.**

## O que o Foster é

Atualmente, o Foster possui uma pequena aplicação web funcional composta por:

- **Aplicação server-side** com Express e Handlebars;
- **Persistência em SQLite** para estabelecimentos cadastrados;
- **Visualização em mapa** utilizando Leaflet e mapas do OpenStreetMap;
- **Cadastro de estabelecimentos** por formulário web;
- **Página de detalhes** com imagens, horários, contato e localização;
- **Suporte de acessibilidade** por meio da integração com o VLibras;
- **Testes automatizados de navegador** com Selenium e Python;
- **Documentação OpenAPI/Swagger** das rotas atuais.

## O que o Foster não é

O projeto atual não implementa os principais módulos esperados de um ERP completo, como:

- autenticação e autorização de usuários;
- perfis, papéis e permissões;
- clientes e fornecedores;
- produtos e controle de estoque;
- compras e vendas;
- contas a pagar e receber;
- faturamento e operações fiscais;
- gestão financeira;
- dashboards e relatórios gerenciais;
- trilhas de auditoria;
- gestão multiempresa;
- uma API REST pública e madura.

Esses recursos podem fazer parte da evolução futura do projeto, mas **não fazem parte da implementação atual**.

## Arquitetura atual

Nesta etapa, o Foster utiliza uma arquitetura pequena e direta:

~~~
Navegador
   │
   ▼
Servidor Express
   │
   ├── Views Handlebars
   ├── Rotas da aplicação
   └── Banco SQLite
~~~

### Principais componentes

- **Node.js** — ambiente de execução JavaScript.
- **Express** — servidor web e roteamento.
- **Handlebars** — renderização HTML no servidor.
- **SQLite** — banco de dados relacional local.
- **Leaflet** — renderização do mapa interativo.
- **OpenStreetMap** — provedor dos tiles do mapa.
- **Swagger UI / OpenAPI** — documentação das rotas.
- **VLibras** — suporte de acessibilidade em Libras.
- **Selenium + Python** — automação de navegador e testes funcionais.

## Principais rotas

| Rota | Finalidade |
|---|---|
| `/` | Página inicial da aplicação |
| `/stores` | Lista e mapa dos estabelecimentos |
| `/store?id=<id>` | Visualização dos detalhes de um estabelecimento |
| `/create-store` | Formulário de cadastro |
| `/save-store` | Persistência de um novo estabelecimento |
| `/api-docs` | Documentação OpenAPI/Swagger |

## Modelo de dados

O banco atual é intencionalmente pequeno e está concentrado na entidade `stores`.

Os registros armazenam informações como:

- coordenadas geográficas;
- nome do estabelecimento;
- descrição;
- número de WhatsApp/contato;
- URLs de imagens;
- informações sobre produtos ou acesso;
- horário de atendimento;
- atendimento aos finais de semana.

Esse modelo atende ao escopo atual de diretório e localização, mas **ainda não representa um domínio empresarial de ERP**.

## Testes

O repositório possui scripts em Python com Selenium para automação do navegador e testes funcionais.

Entre os exemplos atuais estão:

- cadastro automatizado de estabelecimentos;
- submissão repetida de formulários para testes de volume;
- navegação entre as páginas da aplicação;
- testes de interação com o VLibras.

Essa estrutura é útil para validar o protótipo atual, mas ainda não constitui uma estratégia completa de testes unitários, integração e end-to-end.

## Como executar localmente

### Pré-requisitos

- [Node.js](https://nodejs.org/)
- [NPM](https://www.npmjs.com/)
- [Git](https://git-scm.com/) — opcional, mas recomendado

### 1. Clone o repositório

~~~bash
git clone https://github.com/JacanaFSilva/Foster.git
cd Foster
~~~

### 2. Instale as dependências

~~~bash
npm install
~~~

### 3. Inicie a aplicação

~~~bash
npm start
~~~

A aplicação será disponibilizada em:

~~~text
http://localhost:3000
~~~

A documentação Swagger pode ser acessada em:

~~~text
http://localhost:3000/api-docs
~~~

Para desenvolvimento com reinicialização automática:

~~~bash
npm run dev
~~~

## Aplicação online

- **Deploy principal:** https://fosterstores.onrender.com
- **Deploy de testes:** https://foster-7u8w.onrender.com/

> Os ambientes online podem diferir do ambiente local e não devem ser tratados como garantia de persistência de dados de produção.

## Estrutura do projeto

~~~
Foster/
├── public/                 # Arquivos estáticos, CSS, JavaScript e imagens
├── src/
│   ├── database/           # Configuração SQLite e persistência
│   ├── views/              # Templates Handlebars
│   ├── pages.js            # Manipuladores das rotas
│   ├── server.js           # Servidor Express
│   └── swagger.json        # Documentação OpenAPI
├── Templates/              # Templates alternativos da aplicação
├── test/                    # Automação Selenium/Python
├── package.json
├── README.md
└── README-pt.md
~~~

## Status atual

O Foster é uma **aplicação web funcional de pequeno porte**, mas deve ser entendido como uma base/protótipo e não como uma plataforma empresarial finalizada.

Os principais pontos fortes da implementação atual são:

- arquitetura simples;
- fluxo de uso claro;
- cadastro e visualização de estabelecimentos;
- integração com mapas;
- persistência local;
- automação funcional básica;
- facilidade para customizar a camada visual.

Antes de ampliar o projeto para uma plataforma empresarial maior, a base técnica deve ser fortalecida em áreas como:

- utilização de consultas parametrizadas;
- autenticação e autorização;
- validação de entradas e tratamento de erros;
- migrations e infraestrutura de persistência mais robusta;
- ampliação da cobertura de testes;
- configuração por ambiente;
- modelagem orientada ao domínio;
- auditoria e segurança operacional.

## Direção futura

A evolução de longo prazo do Foster pode levar o projeto de um sistema de cadastro e localização de estabelecimentos para uma plataforma de gestão empresarial mais ampla.

Uma possível trajetória seria:

~~~
Gestão de Estabelecimentos
        │
        ▼
Usuários / Perfis / Permissões
        │
        ▼
Clientes / Fornecedores / Produtos
        │
        ▼
Estoque / Compras / Vendas
        │
        ▼
Gestão Financeira
        │
        ▼
Relatórios / Dashboards / Auditoria
~~~

Essa trajetória representa **escopo futuro**, e não funcionalidades atualmente implementadas no repositório.

## Licença

Este projeto é distribuído sob a licença presente no repositório.
