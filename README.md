# Common Library (`tool-common-library`)

**Common Library** es una librería transversal diseñada para centralizar utilidades, configuraciones base y código repetitivo para el ecosistema de proyectos RESTful de `com.ssdjr2.sbc`.

Su objetivo es acelerar el desarrollo de nuevos microservicios proporcionando una base sólida construida sobre **Java 21**, **Spring Framework 6** y **Spring Boot 3**.

## 🛠 Tech Stack

El proyecto utiliza las últimas versiones estables del ecosistema Spring y herramientas de productividad:

* **Core:** Java 21 (LTS)
* **Framework:** Spring Boot 3.5.8 (Spring Framework 6)
* **Persistencia:** Spring Data JPA + Hibernate Validator
* **Seguridad:** Spring Security
* **Mapping:** MapStruct 1.5.5.Final
* **Boilerplate reduction:** Project Lombok
* **Utilities:** Apache Commons Lang3

## 📦 Instalación

Para utilizar esta librería en otros proyectos (microservicios), añade la siguiente dependencia en el `pom.xml` de la aplicación consumidora:

```xml
<dependency>
    <groupId>com.ssdjr2.sbc</groupId>
    <artifactId>tool-common-library</artifactId>
    <version>0.0.2-SNAPSHOT</version>
</dependency>
```

## ✨ Capacidades Incluidas

Al heredar o importar esta librería, tu proyecto obtiene soporte inmediato para:

### 1. Web & API REST
* Dependencias transitivas de `spring-boot-starter-web`.
* Estandarización de respuestas HTTP, manejo de excepciones, manejo de loggers.

### 2. Persistencia y Validación
* **JPA:** Configuración lista para repositorios y entidades.
* **Validación:** Integración de `hibernate-validator` para validación de DTOs y Entidades (`@NotNull`, `@Size`, etc.).

### 3. Seguridad
* Dependencias de `spring-boot-starter-security` para implementación de filtros, autenticación JWT o manejo de sesiones.

### 4. Transformación de Datos (DTO <-> Entity)
* Integración preconfigurada de **Lombok** y **MapStruct**.
* Se utiliza una clase base para los **Mappers**.

### 5. Utilidades
* **UDateTimeService:** Servicio para la gestión de fechas.
* **UJsonAdapter:** Conversor de json como string a class y viceversa.
* **UMethods:** Métodos comunes de utilidad.

## 🚀 Desarrollo y Contribución

### Prerrequisitos
* JDK 21 instalado.
* Maven Compiler 3.11.0 o superior.

### Construcción Local

Para compilar la librería e instalarla en tu repositorio local de Maven para que otros proyectos puedan verla:

```bash
mvn clean install
```

### Notas para Desarrolladores

* **Lombok & MapStruct:** Si añades nuevos mappers, recuerda que la configuración del `maven-compiler-plugin` debe respetar el orden de los *annotation processors* (Lombok primero, Mapstruct después) para evitar problemas de generación de código.
* **Testing:** El proyecto incluye `spring-boot-starter-test` (JUnit 5 + Mockito). Asegúrate de que cualquier nueva utilidad tenga una cobertura de tests unitarios adecuada antes de subir cambios.

## 📄 Estructura del Proyecto (Sugerida)

Dado que es una librería común, el ms que la importe debería mantener una estructura de paquetes agnóstica a las funcionalidades que proporciona:

```text
com.ssdjr2.sbc.xxx
├── config        # Configuraciones globales (Auth, Doc, Ex, Interceptors, Properties, Beans, etc).
├── controllers   # Controladores para la capa presentación.
├── models        # DTOs, Enums, Entities, Mappers, Validations, etc.
├── repositories  # Repositorios, Filtros, etc para la capa de datos.
├── services      # Servicios para la capa de negocio.
└── util          # Clases estáticas de utilidad.
```

## 📝 Licencia

Este proyecto es propiedad de `com.ssdjr2.sbc`.
