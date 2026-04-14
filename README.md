# TCF5 Discovery Server

Este projeto é um servidor de descoberta de serviços baseado no Netflix Eureka, desenvolvido com Spring Boot. Ele permite que microserviços se registrem e descubram uns aos outros em uma arquitetura distribuída.

## Tecnologias Utilizadas

- **Java**: 21
- **Spring Boot**: 4.0.5
- **Spring Cloud**: 2025.1.1
- **Netflix Eureka Server**: Para descoberta de serviços
- **Spring Boot Actuator**: Para monitoramento e métricas

## Pré-requisitos

- Java 21 ou superior
- Maven 3.6+ ou use o wrapper Maven incluído (`./mvnw`)

## Como Executar

### Usando Maven Wrapper

```bash
./mvnw spring-boot:run
```

### Usando Maven (se instalado globalmente)

```bash
mvn spring-boot:run
```

### Compilando e Executando

```bash
./mvnw clean package
java -jar target/tcf5-discovery-server-0.0.1-SNAPSHOT.jar
```

O servidor será iniciado na porta **8761**.

## Configuração

A configuração básica está definida no arquivo `src/main/resources/application.yaml`:

```yaml
server:
  port: 8761

spring:
  application:
    name: tcf5-discovery-server
```

## Dashboard do Eureka

Após iniciar o servidor, você pode acessar o dashboard do Eureka em:

[http://localhost:8761](http://localhost:8761)

## Endpoints do Actuator

O Spring Boot Actuator fornece endpoints para monitoramento:

- **Health Check**: `http://localhost:8761/actuator/health`
- **Info**: `http://localhost:8761/actuator/info`
- **Metrics**: `http://localhost:8761/actuator/metrics`

## Registro de Serviços

Outros microserviços podem se registrar neste servidor de descoberta adicionando a dependência do Eureka Client e configurando a URL do servidor:

```yaml
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/
```

## Documentação

- [Documentação Oficial do Spring Boot](https://docs.spring.io/spring-boot/4.0.5/reference/)
- [Spring Cloud Netflix Eureka](https://docs.spring.io/spring-cloud-netflix/reference/spring-cloud-netflix.html#spring-cloud-eureka-server)
- [Guia de Registro e Descoberta de Serviços](https://spring.io/guides/gs/service-registration-and-discovery/)

## Estrutura do Projeto

```
tcf5-discovery-server/
├── src/
│   ├── main/
│   │   ├── java/com/devrenno/tcf5/discovery/server/
│   │   │   └── Application.java
│   │   └── resources/
│   │       └── application.yaml
│   └── test/
│       └── java/com/devrenno/tcf5/discovery/server/
│           └── ApplicationTests.java
├── pom.xml
├── mvnw
├── mvnw.cmd
└── HELP.md
```

## Desenvolvimento

Para contribuir ou modificar o projeto:

1. Clone o repositório
2. Faça suas alterações
3. Execute os testes: `./mvnw test`
4. Compile: `./mvnw clean compile`
5. Execute: `./mvnw spring-boot:run`
