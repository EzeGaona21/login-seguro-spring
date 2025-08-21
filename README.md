# Login Seguro Spring (Boot 3)

Proyecto minimalista con **login y registro** usando:
- Spring Boot 3 (Web, Security, Thymeleaf)
- Spring Data JPA
- **H2 en memoria** por defecto (funciona sin instalar nada)
- Usuario demo: `admin / 1234`

## Correr
```bash
mvn spring-boot:run
```
Ir a: http://localhost:8080

## Cambiar a MySQL (opcional)
En `src/main/resources/application.properties` reemplazá por:

```
spring.datasource.url=jdbc:mysql://localhost:3306/login_db?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=TU_PASSWORD
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.h2.console.enabled=false
```

Agregá también la dependencia en `pom.xml`:

```
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-j</artifactId>
  <scope>runtime</scope>
</dependency>
```

## Endpoints
- `GET /login` → formulario de login
- `GET /register` / `POST /register` → crear usuario (se guarda en BD)
- `GET /` → home (requiere login)

## Notas
- La contraseña se guarda **encriptada con BCrypt** cuando te registrás.
- Si es la primera vez, se crea un usuario `admin / 1234` automáticamente.
