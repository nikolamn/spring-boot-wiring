# Spring Boot Wiring

## Overview

Demo shows how Spring Boot wires the core automatically — like DataSource, JPA, transactions, MVC, validation — but also how things can be overriden manually if needed
H2 in-memory DB is used

---

## Key Concepts

- **Auto-configured beans**: 
    * DataSource, EntityManagerFactory, TransactionManager, DispatcherServlet, RequestMappingHandlerMapping, Validator 
- **Manual overrides**: 
    * `ManualBeansConfig` shows how to replace auto-configured beans if needed, all commented by default  
- **Properties**: 
    * `GreetingProperties` binds `app.greeting.prefix` from `application.yml`, default is `"Hello"`, overridden by yml  
- **Validation**: 
    * `GreetingService` validates input using Boot’s auto Validator 
- **JPA + H2**: 
    * `Person` entity persists in H2, tables auto-created, accessible via `/person` endpoints.  
- **REST**: 
    * `PersonController` exposes CRUD endpoints, Boot wires DispatcherServlet + handler mapping automatically

---

## How to Test

1. **H2 Console**: `http://localhost:8080/h2-console`  
2. **REST**: `POST /person/new?name=anna`, `GET /person/all`  
3. **Greeting Service**: `/greet?name=Mark` → `"Welcome, Mark"`  
4. **Inspect beans**: `BeanInspectorConfig` prints all main beans at startup  

---
