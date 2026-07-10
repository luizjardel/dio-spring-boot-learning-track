# 💰 API Inteligente para Controle Financeiro com Spring AI e Ollama

Projeto desenvolvido durante o Bootcamp **Java + Spring Boot** da **DIO (Digital Innovation One)**.

O objetivo deste projeto é criar uma API para gerenciamento de transações financeiras utilizando **Spring Boot**, **Spring AI** e um **modelo de linguagem (LLM)** para permitir a interação em linguagem natural.

---

# 📖 Sobre o projeto

A aplicação permite cadastrar e consultar transações financeiras através de endpoints REST e também conversar com a IA para executar essas operações utilizando comandos em linguagem natural.

Toda a arquitetura do projeto foi mantida seguindo os princípios apresentados durante o módulo, separando responsabilidades entre:

- Domain
- Application (Use Cases)
- Infrastructure
- HTTP Controllers

Essa organização facilita a manutenção, escalabilidade e reutilização do código.

---

# 🚀 Tecnologias utilizadas

- Java 25
- Spring Boot
- Spring AI
- Ollama
- H2 Database
- Spring Data JPA
- Gradle
- Lombok

---

# 🤖 Inteligência Artificial

A integração com IA foi realizada utilizando o **Spring AI** juntamente com o **Ollama**, permitindo executar modelos de linguagem localmente.

O endpoint `/transactions/chat` recebe uma mensagem em linguagem natural e utiliza o modelo configurado para interpretar o comando e acionar automaticamente os casos de uso da aplicação.

Exemplo:

```
Cadastre uma despesa de R$ 120,00 com alimentação.
```

ou

```
Liste todas as despesas da categoria MORADIA.
```

---

# 🔄 Alterações realizadas

Durante o desenvolvimento do projeto optei por realizar algumas adaptações em relação à implementação apresentada nas aulas.

A versão original utilizava os serviços da OpenAI para reconhecimento e síntese de voz.

Como essas funcionalidades dependem de créditos na API da OpenAI, adaptei o projeto para utilizar o **Ollama**, permitindo executar o modelo de IA localmente, sem custos.

As principais modificações foram:

- substituição da OpenAI pelo Ollama;
- configuração do Spring AI para execução local;
- manutenção da arquitetura original do projeto;
- preservação do endpoint de chat utilizando IA local;
- adaptação do endpoint responsável pela transcrição de áudio.

O endpoint `/transactions/ai` permanece disponível apenas como demonstração da funcionalidade prevista originalmente, retornando uma mensagem informativa.

Essa adaptação permitiu concluir o desafio mantendo a proposta do projeto e possibilitando sua execução sem depender de serviços pagos.

---

# 📂 Estrutura do projeto

```
src
 ├── application
 │     ├── Use Cases
 │
 ├── domain
 │     ├── Entidades
 │     ├── Repositórios
 │
 ├── infrastructure
 │     ├── persistence
 │     ├── http
 │     └── configuração
 │
 └── resources
       ├── application.properties
       └── prompts
```

---

# 📌 Endpoints

## Criar transação

```
POST /transactions
```

Exemplo:

```json
{
  "description": "Mercado",
  "value": 120.50,
  "category": "FOOD"
}
```

---

## Listar por categoria

```
GET /transactions/{category}
```

Exemplo:

```
GET /transactions/FOOD
```

---

## Chat com IA

```
POST /transactions/chat
```

Exemplo de requisição:

```
Cadastre uma despesa de R$ 85,00 de transporte.
```

---

## Transcrição de áudio

```
POST /transactions/ai
```

Nesta adaptação o endpoint retorna uma mensagem informativa, pois a implementação original dependia dos serviços de reconhecimento de voz da OpenAI.

---

# ▶️ Como executar

## 1. Clone o repositório

```bash
git clone https://github.com/SEU-USUARIO/dio-spring-boot-learning-track.git
```

---

## 2. Acesse o módulo

```bash
cd 05-spring-ai/budgeting
```

---

## 3. Execute o Ollama

Exemplo utilizando o modelo Gemma:

```bash
ollama run gemma3
```

ou outro modelo compatível configurado na aplicação.

---

## 4. Execute o projeto

```bash
./gradlew bootRun
```

ou

```bash
gradlew bootRun
```

---

# 💡 Aprendizados

Durante este projeto foi possível praticar conceitos importantes como:

- Arquitetura em camadas;
- Spring Boot;
- Spring AI;
- Integração com LLMs;
- Injeção de Dependência;
- Spring Data JPA;
- REST APIs;
- Engenharia de Prompts;
- Ferramentas (Tools) do Spring AI.

Além disso, o projeto proporcionou experiência na adaptação de soluções para diferentes provedores de IA, mantendo a mesma arquitetura da aplicação.

---

# 📝 Observações

Este projeto foi desenvolvido com fins educacionais durante o Bootcamp da DIO.

A estrutura principal segue a proposta apresentada no curso, porém foram realizadas adaptações para permitir sua execução utilizando modelos locais através do Ollama, eliminando a dependência de créditos da OpenAI.

---

# 👨‍💻 Autor

**Luiz Jardel do Nascimento**

- GitHub: https://github.com/luizjardel
- LinkedIn: https://www.linkedin.com/in/luiz-jardel/