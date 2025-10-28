# INKFLOW Backend API

Backend Spring Boot para o sistema INKFLOW - Plataforma de agendamento de tatuagens.

## 🚀 Tecnologias

- Java 17
- Spring Boot 3.5.6
- Spring Data JPA
- SQL Server
- Maven

## 📋 Estrutura do Projeto

```
src/main/java/com/backend/INKFLOW/
├── config/
│   └── CorsConfig.java           # Configuração CORS
├── controller/
│   ├── AgendamentoController.java # Endpoints de agendamentos
│   ├── AuthController.java        # Autenticação
│   ├── ClienteController.java     # CRUD de clientes
│   └── HealthController.java      # Health check
├── model/
│   ├── Agendamento.java          # Entidade Agendamento
│   └── Cliente.java              # Entidade Cliente
├── repository/
│   ├── AgendamentoRepository.java
│   └── ClienteRepository.java
├── service/
│   ├── AgendamentoService.java
│   └── ClienteService.java
└── InkflowApplication.java       # Classe principal
```

## 🔧 Configuração

### Banco de Dados

Configure as credenciais em `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:sqlserver://SEU_HOST:1433;databaseName=INKFLOW
spring.datasource.username=SEU_USUARIO
spring.datasource.password=SUA_SENHA
```

### Executar Script SQL

Execute o arquivo `script-simples.sql` no seu SQL Server para criar as tabelas.

## 🏃 Como Executar

### Localmente

```bash
# Compilar
./mvnw clean package

# Executar
./mvnw spring-boot:run
```

### Docker

```bash
# Build
docker build -t inkflow-backend .

# Run
docker run -p 8080:8080 inkflow-backend
```

## 📡 Endpoints

### Health Check
- `GET /` - Status da API
- `GET /health` - Health check
- `GET /ping` - Teste de conectividade

### Autenticação
- `POST /api/auth/login` - Login de usuário

### Clientes
- `GET /api/clientes` - Listar todos
- `GET /api/clientes/{id}` - Buscar por ID
- `POST /api/clientes` - Criar cliente
- `PUT /api/clientes/{id}` - Atualizar cliente
- `DELETE /api/clientes/{id}` - Deletar cliente

### Agendamentos
- `GET /api/agendamentos` - Listar todos
- `GET /api/agendamentos/{id}` - Buscar por ID
- `GET /api/agendamentos/status/{status}` - Buscar por status
- `POST /api/agendamentos` - Criar agendamento
- `PUT /api/agendamentos/{id}` - Atualizar agendamento
- `DELETE /api/agendamentos/{id}` - Deletar agendamento

## 🔐 Credenciais Admin

```
Email: admin@inkflow.com
Senha: admin123
```

## 🌐 Deploy

O backend está configurado para deploy no Render.com com as seguintes variáveis de ambiente:
- `PORT` - Porta do servidor (padrão: 8080)
- Credenciais do banco configuradas no application.properties

## 📝 Notas

- CORS configurado para `https://inkflowfrontend.vercel.app` e `http://localhost:5173`
- Senhas armazenadas em texto plano (implementar hash em produção)
- JPA configurado com `ddl-auto=none` (usar scripts SQL)
