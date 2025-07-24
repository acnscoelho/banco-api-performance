# banco-api-performance

Repositório de testes de performance utilizando JavaScript e [K6](https://k6.io/) para APIs bancárias.

Repositório: [https://github.com/acnscoelho/banco-api-performance](https://github.com/acnscoelho/banco-api-performance)

---

## Introdução

Este projeto tem como objetivo realizar testes de performance em APIs bancárias, utilizando o K6 para simular cenários de carga e validar o desempenho dos endpoints. Os scripts são escritos em JavaScript, facilitando a customização e manutenção dos testes.

---

## Tecnologias Utilizadas

- [K6](https://k6.io/) — Ferramenta open source para testes de carga e performance.
- JavaScript — Linguagem dos scripts de teste.

---

## Estrutura do Repositório

```
├── config/
│   └── config.local.json
├── fixtures/
│   └── postLogin.json
├── helpers/
│   └── autenticacao.js
├── tests/
│   ├── login.test.js
│   └── transferencias.test.js
├── utils/
│   └── variaveis.js
└── README.md
```

---

## Objetivo de cada grupo de arquivos

- **config/**: Arquivos de configuração, como a URL base da API (`config.local.json`).
- **fixtures/**: Dados estáticos para uso nos testes, como payloads de login.
- **helpers/**: Funções auxiliares reutilizáveis, por exemplo, autenticação e obtenção de token.
- **tests/**: Scripts de teste de performance, cada arquivo representa um cenário ou endpoint a ser testado.
- **utils/**: Utilitários gerais, como funções para obter variáveis de ambiente ou configurações.

---

## Modo de Instalação e Execução do Projeto

### 1. Instalação do K6

Você pode instalar o K6 de diferentes formas, dependendo do seu sistema operacional:

- **Windows**:
  - Usando Chocolatey: `choco install k6`
  - Usando Winget: `winget install k6 --source winget`
- **MacOS**:
  - Usando Homebrew: `brew install k6`
- **Linux**:
  - [Veja instruções detalhadas na documentação oficial](https://grafana.com/docs/k6/latest/set-up/install/)
- **Docker**:
  - `docker pull grafana/k6`

### 2. Configuração da variável de ambiente BASE_URL

O endereço da API a ser testada deve ser informado via variável de ambiente `BASE_URL`. Caso não seja definida, será utilizado o valor presente em `config/config.local.json`.

Exemplo de uso:

```sh
set BASE_URL=http://localhost:3000   # Windows (cmd)
export BASE_URL=http://localhost:3000 # Linux/Mac
```

### 3. Execução dos testes

Para rodar um teste, utilize o comando:

```sh
k6 run tests/login.test.js
```

ou

```sh
k6 run tests/transferencias.test.js
```

### 4. Acompanhamento do relatório em tempo real e exportação

O K6 permite acompanhar o relatório em tempo real via dashboard web e exportar o resultado em HTML. Para isso, utilize as variáveis de ambiente do próprio K6:

```sh
K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/login.test.js
```

- `K6_WEB_DASHBOARD=true`: Habilita o dashboard web em tempo real.
- `K6_WEB_DASHBOARD_EXPORT=html-report.html`: Exporta o relatório ao final da execução para o arquivo `html-report.html`.

---

## Referências
- [Documentação oficial do K6](https://k6.io/docs/)
- [Repositório no GitHub](https://github.com/acnscoelho/banco-api-performance)
