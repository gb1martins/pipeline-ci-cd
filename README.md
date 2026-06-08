# Pipeline CI/CD com GitHub Pages

Este projeto demonstra a implementação de um pipeline de Integração Contínua (CI) e Entrega Contínua (CD) utilizando **GitHub Actions** para automatizar o deploy de um site estático no **GitHub Pages**.

## 🎯 Objetivo

O objetivo principal deste projeto é automatizar o ciclo de vida de desenvolvimento de uma página web simples, garantindo que:
1.  Cada alteração no código seja validada automaticamente.
2.  O deploy seja realizado apenas se os critérios de qualidade (validação) forem atendidos.
3.  A intervenção manual para publicação seja eliminada.

## 🏗️ Arquitetura do Pipeline

A arquitetura é composta por dois workflows que trabalham de forma encadeada:

### 1. CI Pipeline (Integração Contínua)
- **Gatilho:** Executado em cada `push` ou `pull_request` para a branch `main`.
- **Ações:**
    - Faz o checkout do código.
    - Valida se o arquivo essencial `site/index.html` existe.
    - Gera um artefato de build (`site-html`) para ser utilizado nas etapas seguintes.

### 2. CD Pipeline (Entrega Contínua)
- **Gatilho:** Executado automaticamente após a conclusão bem-sucedida do **CI Pipeline**.
- **Ações:**
    - Configura o ambiente do GitHub Pages.
    - Faz o upload dos arquivos da pasta `site/` como um artefato de publicação.
    - Realiza o deploy oficial no GitHub Pages.

## 📁 Estrutura do Projeto

```text
pipeline-ci-cd/
├── site/
│   └── index.html          # Conteúdo do site
└── .github/
    └── workflows/
        ├── ci.yml          # Definição da Integração Contínua
        └── cd.yml          # Definição do Deploy Contínuo
```

## 🚀 Como funciona

1.  Você faz uma alteração no arquivo `index.html`.
2.  Ao dar `git push`, o **CI Pipeline** entra em ação.
3.  Se a validação passar, o **CD Pipeline** é disparado.
4.  Em poucos instantes, seu site é atualizado automaticamente na URL do GitHub Pages do seu repositório.
