# Desafio Dio - Criando seu Primeiro Projeto de Devops com GitLab



O DevOps é uma abordagem de desenvolvimento de software que enfatiza a colaboração entre desenvolvedores e operações. O GitLab é uma plataforma DevOps que fornece um conjunto completo de ferramentas para gerenciamento de código, rastreamento de problemas, integração contínua e entrega contínua (CI/CD).

Neste projeto, criaremos um projeto de DevOps completo com o GitLab, incluindo um pipeline de CI/CD para compilar, testar e implantar nosso código.



### **Pré-requisitos**

- Conta do GitLab
- Editor de código
- Linha de comando



### **Passos**



### **1. Criar um Projeto GitLab**

- Acesse o GitLab e crie um novo projeto.
- Nomeie seu projeto e selecione um modelo (por exemplo, "Projeto de Software").



### **2. Configurar o Repositório Git**



- Crie um novo repositório Git local no seu computador.
- Adicione arquivos ao seu repositório e faça commit das alterações.
- Vincule seu repositório local ao repositório remoto do GitLab.



### **3. Criar um Pipeline de CI/CD**



- Crie um arquivo `.gitlab-ci.yml` na raiz do seu projeto.
- Defina os estágios e tarefas do seu pipeline de CI/CD.
- Por exemplo, você pode definir um estágio de construção para compilar seu código, um estágio de teste para executar testes unitários e um estágio de implantação para implantar seu código em um servidor.



### **4. Configurar o Pipeline de CI/CD (continuação)**

Aqui está um exemplo de um arquivo `.gitlab-ci.yml`:

yaml



```yaml
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
```



### **5. Executar o Pipeline de CI/CD**



- Faça push das alterações para o seu repositório remoto do GitLab.

- O GitLab iniciará automaticamente o pipeline de CI/CD.

- Você pode monitorar o progresso do pipeline no painel do GitLab.

  

### **6. Monitore e Melhore**



- Monitore os resultados do seu pipeline de CI/CD para identificar quaisquer problemas ou gargalos.
- Faça ajustes no seu pipeline conforme necessário para melhorar a eficiência e a qualidade.



## ou Aprimorando:



## 1. Configurando o Ambiente



Antes de começarmos, certifique-se de ter o GitLab instalado e uma conta criada. Se você ainda não tem uma conta, pode se cadastrar gratuitamente no [GitLab](https://gitlab.com/). Agora, vamos aos passos:



### 1.1. Instalando o Git



O primeiro passo é instalar o Git em seu ambiente de desenvolvimento. O Git é uma ferramenta essencial para controle de versão. Você pode baixá-lo gratuitamente no [site oficial](https://git-scm.com/). Após a instalação, verifique a versão do Git executando o comando:

```
git --version
```



### 1.2. Criando um Grupo no GitLab



1. Faça login no GitLab.
2. Clique em "Groups" no menu superior e selecione "New group".
3. Preencha as informações do grupo, como nome e descrição. Lembre-se de selecionar a opção "Private" para tornar os repositórios privados.
4. Clique em "Create group".



### 1.3. Adicionando Membros ao Grupo



1. No dashboard do grupo, clique em "Members" no lado esquerdo.
2. Adicione os membros que participarão do projeto. Eles precisam ter uma conta no GitLab.



## 2. Criando o Repositório

### 

Agora, vamos criar o repositório para o nosso projeto:

1. Acesse o grupo que você criou.
2. Clique em "New project" e escolha um nome para o projeto.
3. Selecione a opção "Private" para manter o código seguro.
4. Crie o projeto.



### 3. Definindo o Pipeline com .gitlab-ci.yml



O arquivo `.gitlab-ci.yml` é onde definimos os jobs do pipeline. Vamos criar um exemplo simples:

```
# .gitlab-ci.yml

build-job:
  stage: build
  script:
    - echo "Hello, $GITLAB_USER_LOGIN!"

test-job1:
  stage: test
  script:
    - echo "This job tests something"

test-job2:
  stage: test
  script:
    - echo "This job tests something, but takes more time than test-job1."
    - echo "After the echo commands complete, it runs the sleep command for 20 seconds"
    - echo "which simulates a test that runs 20 seconds longer than test-job1"
    - sleep 20

deploy-prod:
  stage: deploy
  script:
    - echo "This job deploys something from the $CI_COMMIT_BRANCH branch."
  environment: production
```



Neste exemplo, temos quatro jobs: `build-job`, `test-job1`, `test-job2` e `deploy-prod`. Os comentários nas mensagens `echo` são exibidos na interface do GitLab quando você visualiza os jobs. As variáveis predefinidas, como `$GITLAB_USER_LOGIN` e `$CI_COMMIT_BRANCH`, são preenchidas quando os jobs são executados.



### 4. Executando o Pipeline



Após criar o arquivo `.gitlab-ci.yml`, faça um commit no repositório. O GitLab executará automaticamente os jobs definidos no pipeline. Você pode acompanhar o progresso na seção "CI/CD > Pipelines" do seu projeto.









### **Conclusão**



Neste projeto, criamos um projeto de DevOps completo com o GitLab, incluindo um pipeline de CI/CD para compilar, testar e implantar nosso código. Ao adotar o DevOps com o GitLab, podemos melhorar a colaboração, a eficiência e a qualidade do nosso desenvolvimento de software.
