# Projeto de Qualidade Educacional

Este é um projeto educacional em Java usando Spring Boot e Maven para ensinar conceitos de qualidade aos alunos. O projeto implementa um sistema simples de cadastro de alunos e professores com uma interface web básica.

## Funcionalidades

- Cadastro e gerenciamento de alunos
- Cadastro e gerenciamento de professores
- Interface web simples usando Thymeleaf e Bootstrap
- Banco de dados MongoDB para armazenamento de documentos

## Tecnologias Utilizadas

- Java 17
- Spring Boot 3.2.0
- Maven
- Spring Data MongoDB
- Thymeleaf
- Bootstrap
- Banco de Dados MongoDB

## Conexão ao Banco de Dados

A conexão MongoDB é fornecida pela variável de ambiente `MONGODB_URI` do processo
que inicia a aplicação. `src/main/resources/application.properties` usa
`spring.data.mongodb.uri=${MONGODB_URI}`, sem URI ou credenciais padrão no código.
Defina essa variável antes de executar a aplicação; mantenha o valor real no
ambiente privado ou no gerenciador de segredos da hospedagem.

### Configuração local

Para uma instância MongoDB de desenvolvimento já disponível na própria máquina,
o exemplo abaixo usa somente loopback e uma base local, sem credenciais reais.
Ele não instala nem inicia o MongoDB.

No PowerShell, no mesmo terminal que iniciará a aplicação:

```powershell
$env:MONGODB_URI = 'mongodb://127.0.0.1:27017/educational_quality_local'
```

No Bash:

```bash
export MONGODB_URI='mongodb://127.0.0.1:27017/educational_quality_local'
```

Depois, execute um dos comandos Maven da seção abaixo. O projeto não carrega arquivos `.env` automaticamente;
criar esse arquivo ou copiar um modelo não define a variável no processo.
Para um banco remoto próprio, injete a URI privadamente, sem colá-la em arquivos
versionados, documentação ou logs. Não reutilize credenciais anteriormente divulgadas.

A remoção da URI do código não revoga credenciais nem remove versões do histórico.
O responsável pelo banco deve identificar o ambiente e a conta correspondentes,
substituir ou revogar o acesso utilizado e avaliar reutilização. Esta correção não
conectou ao banco nem verificou a validade dos dados publicados.

## Começando

### Pré-requisitos

- Java 17 ou superior
- Maven 3.6.0 ou superior

### Instalação do Maven

#### No Windows:
1. Baixe o Maven do site oficial: https://maven.apache.org/download.cgi
2. Extraia o arquivo ZIP para um diretório como `C:\apache-maven-3.9.5`
3. Adicione a variável de ambiente `MAVEN_HOME` apontando para o diretório do Maven
4. Adicione `%MAVEN_HOME%\bin` ao seu PATH
5. Verifique a instalação com o comando:
```cmd
mvn -version
```

#### No Linux (Ubuntu/Debian):
```bash
sudo apt update
sudo apt install maven
```

#### No Linux (CentOS/RHEL/Fedora):
```bash
sudo yum install maven
# ou para Fedora:
sudo dnf install maven
```

### Executando a Aplicação

1. Clone o repositório
2. Navegue até o diretório do projeto
3. Defina `MONGODB_URI` no ambiente conforme a seção de configuração.
4. Execute a aplicação usando Maven:

```bash
./mvnw spring-boot:run
```

Ou construa e execute o JAR:

```bash
./mvnw clean package
java -jar target/educational-quality-project-0.0.1-SNAPSHOT.jar
```

### Comandos úteis do Maven

- Para compilar o projeto: `mvn compile`
- Para executar os testes: `mvn test`
- Para empacotar o projeto: `mvn package`
- Para limpar os arquivos gerados: `mvn clean`
- Para executar a aplicação: `mvn spring-boot:run`

### Acessando a Aplicação

Após iniciar a aplicação, você pode acessá-la em:
- Página principal: http://localhost:8080
- Página de alunos: http://localhost:8080/students
- Página de professores: http://localhost:8080/teachers

### API Endpoints

A aplicação também disponibiliza endpoints RESTful para integração com outras aplicações:

#### Estudantes
- `GET /api/students` - Listar todos os estudantes
- `GET /api/students/{id}` - Obter detalhes de um estudante específico
- `POST /api/students` - Criar um novo estudante
- `PUT /api/students/{id}` - Atualizar informações de um estudante
- `DELETE /api/students/{id}` - Excluir um estudante

#### Professores
- `GET /api/teachers` - Listar todos os professores
- `GET /api/teachers/{id}` - Obter detalhes de um professor específico
- `POST /api/teachers` - Criar um novo professor
- `PUT /api/teachers/{id}` - Atualizar informações de um professor
- `DELETE /api/teachers/{id}` - Excluir um professor

## Estrutura do Projeto

- `entity/` - Entidades MongoDB para Aluno e Professor
- `repository/` - Interfaces da camada de acesso a dados
- `service/` - Camada de lógica de negócios
- `controller/` - Controladores web
- `templates/` - Templates Thymeleaf com Bootstrap

## Valor Educacional

Este projeto demonstra:
- Operações CRUD básicas
- Arquitetura MVC
- Fundamentos do Spring Boot
- Uso do Spring Data MongoDB
- Injeção de dependência
- Design de API RESTful
- Integração com banco de dados NoSQL
- Template frontend com Thymeleaf