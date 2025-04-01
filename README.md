# Deploy de uma Aplicação Web Simples usando Docker e GitHub Actions

Este projeto demonstra como configurar um ambiente virtual, containerizar uma aplicação e realizar o deploy automatizado utilizando Docker e GitHub Actions.

## Objetivo
Aprender a configurar um ambiente virtual, containerizar uma aplicação e automatizar o deploy utilizando GitHub Actions.

## Pré-requisitos
- Conta no GitHub
- Docker instalado localmente ou uso do [Play with Docker](https://labs.play-with-docker.com/)
- Conhecimentos básicos de Git, linha de comando e conceitos de CI/CD

## Passos para Configuração

### 1. Criar o Repositório no GitHub
1. Criar um novo repositório chamado **app-deploy-demo**.
2. Clonar o repositório localmente:
   ```sh
   git clone https://github.com/seu-usuario/app-deploy-demo.git
   cd app-deploy-demo
   ```
3. Criar um arquivo `README.md` e adicionar informações do projeto.
4. Criar um arquivo `Dockerfile` para a aplicação.
5. Comitar e enviar as alterações:
   ```sh
   git add .
   git commit -m "Configuração inicial do projeto"
   git push origin main
   ```

### 2. Configurar GitHub Actions
1. Criar a pasta `.github/workflows/` no repositório.
2. Criar o arquivo `deploy.yml` dentro da pasta e adicionar o seguinte código:
   ```yaml
   name: Deploy Application

   on:
     push:
       branches:
         - main

   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout do código
           uses: actions/checkout@v2

         - name: Configurar Docker
           run: |
             docker build -t app-deploy-demo .
             docker run -d -p 8080:8080 app-deploy-demo
   ```
3. Comitar e enviar o arquivo `deploy.yml` para o repositório.

### 3. Executar o Deploy
1. Fazer um `push` para o repositório para acionar o GitHub Actions.
2. Acompanhar a execução do workflow no GitHub Actions.

### 4. Testar a Aplicação
1. Verificar os contêineres em execução:
   ```sh
   docker ps
   ```
2. Testar o acesso à aplicação via navegador ou terminal:
   ```sh
   curl http://localhost:8080
   ```

## Conclusão
Este projeto demonstra como automatizar o deploy de uma aplicação simples utilizando Docker e GitHub Actions. Ele pode ser expandido para projetos mais complexos conforme necessário.

## Recursos de Apoio
- [Documentação do GitHub Actions](https://docs.github.com/en/actions)
- [Docker Hub](https://hub.docker.com/)
- [Play with Docker](https://labs.play-with-docker.com/)

