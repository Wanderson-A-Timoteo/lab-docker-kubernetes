# Laboratório de Docker e Kubernetes - Avaliação 3

Este repositório contém a resolução prática e documentada da infraestrutura/DevOps.

## 👨‍💻 Autor
**Wanderson de Almeida Timóteo**

## 🎯 Objetivo do Projeto
Demonstrar a evolução e o domínio progressivo na orquestração de contentores, partindo da execução manual com Docker, passando pela automação com Docker Compose, até chegar à alta disponibilidade com Kubernetes. 

A aplicação em foco é um sistema simples em **PHP 8.4 (Apache)** que se conecta a uma base de dados **MySQL 9.7** para realizar o registo de pessoas numa tabela.

## 🛠️ Tecnologias Utilizadas
* **Docker** & **Dockerfile**
* **Docker Compose**
* **Kubernetes** (Minikube & `kubectl`)
* **PHP 8.4**
* **MySQL 9.7**

## 📁 Estrutura do Repositório
O projeto está estruturado em três laboratórios progressivos:

* `lab01/`: Contém os ficheiros da aplicação web (`plataforma/`) e o `Dockerfile` para a construção personalizada da imagem do servidor web com a extensão `mysqli`. Cobre a criação manual de redes e contentores (`docker run`).
* `lab02/`: Contém o ficheiro `docker-compose.yml` responsável pela orquestração declarativa. Permite iniciar a base de dados, a rede virtual e a aplicação web de forma simultânea com um único comando.
* `lab03/`: Contém os manifestos YAML do Kubernetes (`app-deployment`, `app-service`, `mysql-deployment`, `mysql-service`) para o lançamento da infraestrutura com múltiplas réplicas, balanceamento de carga e alta disponibilidade através do Minikube.
* `.github/`: Pasta dedicada ao armazenamento das evidências (capturas de ecrã) exigidas em cada etapa da avaliação, comprovando a execução e o funcionamento de todos os passos.

## 🚀 Como Executar

### Laboratório 1: Docker Manual e Dockerfile
1. Navegue até à pasta `lab01`.
2. Construa a imagem: `docker build -t php-plataforma:v1 .`
3. Crie a rede: `docker network create rede-lab-teste-devops`
4. Inicie a base de dados: `docker run -d --name db001 --network rede-lab-teste-devops -e MYSQL_ROOT_PASSWORD=123456 mysql:9.7`
5. Inicie a aplicação web: `docker run -d --name app001 --network rede-lab-teste-devops -p 80:80 php-plataforma:v1`

### Laboratório 2: Docker Compose
1. Navegue até à pasta `lab02`.
2. Execute a orquestração: `docker compose up -d`
3. Aceda a `http://localhost` no seu navegador de internet.
4. Para encerrar: `docker compose down`

### Laboratório 3: Kubernetes (Minikube)
1. Inicie o seu cluster local: `minikube start`
2. Aponte o Docker para o Minikube (Windows): `minikube docker-env | Invoke-Expression`
3. Construa ou carregue a imagem do PHP localmente para o Minikube.
4. Navegue até à pasta `lab03`.
5. Aplique os manifestos: `kubectl apply -f .`
6. Exponha o serviço e aceda no navegador: `minikube service app001`

## 📄 Licença
Este projeto está sob a licença MIT.

