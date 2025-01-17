# Desafio DIO - Criando Seu Primeiro Projeto de DevOps com GitLab

O DevOps é uma abordagem de desenvolvimento de software que promove a colaboração entre as equipes de desenvolvimento e operações. Já o GitLab é uma plataforma que oferece um conjunto completo de ferramentas para gerenciamento de código, rastreamento de problemas, integração contínua e entrega contínua (CI/CD).

Neste desafio, vamos construir um projeto de DevOps completo utilizando o GitLab, incluindo a configuração de um pipeline de CI/CD para compilar, testar e implantar o código.

Pré-requisitos
Conta no GitLab.
Editor de código.
Acesso à linha de comando.
Passos para Criar o Projeto
1. Criar um Projeto no GitLab
Acesse o GitLab e crie um novo projeto.
Dê um nome ao projeto e escolha um modelo (exemplo: "Projeto de Software").
2. Configurar o Repositório Git
No seu computador, crie um novo repositório Git local.
Adicione os arquivos ao repositório e faça o commit das alterações.
Vincule o repositório local ao repositório remoto do GitLab usando:
bash
Copiar
Editar
git remote add origin <URL_DO_REPOSITORIO>
git push -u origin main
3. Configurar o Pipeline de CI/CD
Crie um arquivo .gitlab-ci.yml na raiz do projeto.
Defina os estágios e as tarefas do pipeline, como no exemplo abaixo:
yaml
Copiar
Editar
stages:
  - build
  - test
  - deploy

build:
  image: node:latest
  script:
    - npm install
    - npm run build

test:
  image: node:latest
  script:
    - npm test

deploy:
  image: nginx:latest
  script:
    - mv build/* /usr/share/nginx/html
Neste exemplo:

Build: Compila o código.
Test: Executa testes unitários.
Deploy: Implanta o código em um servidor.
4. Executar o Pipeline
Faça o push do arquivo .gitlab-ci.yml para o repositório remoto:
bash
Copiar
Editar
git add .gitlab-ci.yml
git commit -m "Configuração do pipeline"
git push
O GitLab iniciará automaticamente o pipeline e permitirá monitorar o progresso em CI/CD > Pipelines.
5. Monitorar e Melhorar
Verifique os resultados do pipeline para identificar falhas ou gargalos.
Ajuste as configurações para otimizar a eficiência e a qualidade do processo.
Aprimorando o Projeto
1. Configurar o Ambiente
Instale o Git:

Baixe e instale pelo site oficial.
Confirme a instalação com:
bash
Copiar
Editar
git --version
Crie um Grupo no GitLab:

Faça login no GitLab, clique em Groups > New group, preencha as informações e selecione a opção "Private".
Adicione Membros ao Grupo:

No menu do grupo, clique em Members e adicione colaboradores.
2. Definir um Pipeline Avançado
Exemplo de configuração de .gitlab-ci.yml com múltiplos jobs:
yaml
Copiar
Editar
build-job:
  stage: build
  script:
    - echo "Olá, $GITLAB_USER_LOGIN!"

test-job1:
  stage: test
  script:
    - echo "Testando funcionalidade 1."

test-job2:
  stage: test
  script:
    - echo "Testando funcionalidade 2 com maior tempo de execução."
    - sleep 20

deploy-prod:
  stage: deploy
  script:
    - echo "Implantando no ambiente de produção da branch $CI_COMMIT_BRANCH."
  environment: production
3. Acompanhar e Iterar
Após definir o pipeline, monitore e otimize os jobs regularmente para assegurar o sucesso do projeto.
Conclusão
Neste desafio, aprendemos a criar um projeto completo de DevOps no GitLab, incluindo a configuração de um pipeline de CI/CD. Com essa abordagem, melhoramos a colaboração entre equipes, além de aumentar a eficiência e a qualidade no desenvolvimento de software.
