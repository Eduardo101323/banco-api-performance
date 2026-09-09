# Banco API - Testes de Performance

## Introdução

Este projeto contém testes de performance desenvolvidos em **JavaScript** utilizando o **K6**.

O objetivo do projeto é avaliar o comportamento e o desempenho da API Banco API sob diferentes condições de carga, permitindo analisar métricas como:

- Tempo de resposta das requisições;
- Quantidade de requisições executadas;
- Taxa de erros;
- Desempenho da API durante a execução dos testes;
- Comportamento da aplicação com múltiplos usuários virtuais.

A URL da API utilizada durante a execução dos testes é configurada através da variável de ambiente `BASE_URL`.

Repositório da API testada:

https://github.com/juliodelimas/banco-api

---

## Tecnologias utilizadas

O projeto utiliza as seguintes tecnologias:

- **JavaScript** — Linguagem utilizada para desenvolver os scripts de teste;
- **K6** — Ferramenta utilizada para execução dos testes de performance;
- **Git** — Utilizado para o versionamento do projeto;
- **GitHub** — Utilizado para hospedagem e compartilhamento do repositório.

Documentação oficial do K6:

https://grafana.com/docs/k6/

---

## Estrutura do repositório

```text
banco-api-performance/
│
├── config/
├── fixtures/
├── helpers/
├── tests/
├── utils/
│
├── .gitignore
└── README.md
```

---

## Objetivo de cada grupo de arquivos

### `config/`

Esta pasta contém arquivos relacionados às configurações utilizadas pelos testes.

Podem ser incluídas configurações como:

- Cenários de carga;
- Quantidade de usuários virtuais;
- Duração dos testes;
- Thresholds;
- Outras configurações necessárias para a execução dos testes de performance.

---

### `fixtures/`

Esta pasta contém dados utilizados durante a execução dos testes.

Esses dados podem representar, por exemplo:

- Usuários;
- Contas;
- Valores utilizados nas requisições;
- Dados necessários para criar cenários de teste.

A utilização de fixtures ajuda a manter os dados separados da lógica dos testes.

---

### `helpers/`

Esta pasta contém funções auxiliares utilizadas pelos scripts de teste.

O objetivo é evitar a repetição de código e facilitar a reutilização de funcionalidades comuns entre diferentes testes.

Exemplos:

- Preparação de requisições;
- Criação de headers;
- Funções auxiliares para autenticação;
- Processamento de respostas.

---

### `tests/`

Esta pasta contém os scripts responsáveis pela execução dos testes de performance.

Cada arquivo representa um ou mais cenários de teste que podem ser executados utilizando o K6.

Exemplo de execução:

```bash
k6 run tests/login.test.js
```

---

### `utils/`

Esta pasta contém funções utilitárias que podem ser compartilhadas entre diferentes partes do projeto.

Essas funções ajudam na organização e reutilização do código.

---

## Instalação e execução do projeto

### Pré-requisitos

Antes de executar o projeto, é necessário possuir os seguintes programas instalados:

- Git;
- K6.

Para verificar se o K6 está instalado corretamente, execute:

```bash
k6 version
```

---

### Clonar o repositório

Clone o projeto utilizando o comando:

```bash
git clone https://github.com/Eduardo101323/banco-api-performance.git
```

Entre na pasta do projeto:

```bash
cd banco-api-performance
```

---

### Configurar a variável de ambiente

Os testes utilizam a variável de ambiente `config.local.json` para definir a URL da API que será testada.

No Git Bash, a variável pode ser informada diretamente antes do comando de execução.

Exemplo:

```json
{
    "baseURL": "http://localhost:3000"
}
```

Substitua `http://localhost:3000` pela URL correspondente ao ambiente que deseja testar.

---

### Executar um teste

Para executar um teste específico, utilize:

```bash
k6 run tests/login.test.js
```

No Windows, dependendo do terminal utilizado, a forma de definir variáveis de ambiente pode ser diferente.

#### Git Bash

```bash
k6 run tests/login.test.js
```

---

### Executar o teste com acompanhamento em tempo real

O K6 permite acompanhar os resultados através de um dashboard web durante a execução do teste.

Para habilitar o dashboard, utilize a variável de ambiente:

```bash
BASE_URL=http://localhost:3000 K6_WEB_DASHBOARD=true k6 run tests/login.test.js
```

Durante a execução, o K6 disponibilizará um endereço local para acompanhar as métricas em tempo real através do navegador.

---

### Executar o teste e exportar o relatório HTML

Também é possível exportar os resultados do dashboard para um arquivo HTML.

Exemplo:

```bash
K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
```

Ao final da execução, será gerado o arquivo:

```text
html-report.html
```

Esse arquivo pode ser aberto posteriormente em um navegador para visualizar o relatório do teste.

---

### Execução completa com dashboard e exportação do relatório

Exemplo completo:

```bash
K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/login.test.js
```

Com esse comando:

- A variável `BASE_URL` define a URL da API;
- `K6_WEB_DASHBOARD=true` habilita o acompanhamento das métricas em tempo real;
- `K6_WEB_DASHBOARD_EXPORT=html-report.html` exporta o relatório para um arquivo HTML ao final da execução;
- `tests/login.test.js` define o script de teste que será executado.

---

## Autor

Eduardo Cavalcante

GitHub:

https://github.com/Eduardo101323
