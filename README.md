# Fruits API

This is a Spring Boot application that provides a RESTful API for managing fruits. It allows you to create, read, update, and delete fruits from an H2 in-memory database.

## Project Description

The Fruits API is a simple CRUD (Create, Read, Update, Delete) application built with Spring Boot. It uses an H2 in-memory database to store fruit data. Each fruit has an ID, a name, and a quantity.

## Configuration

The application uses the following configuration:

```properties
spring.application.name=S04T02N01
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
```

### Database Configuration

- **Database**: H2 (in-memory)
- **URL**: jdbc:h2:mem:testdb
- **Driver**: org.h2.Driver
- **Username**: sa
- **Password**: password

### JPA Configuration

- **Show SQL**: true
- **Hibernate DDL Auto**: update
- **Database Platform**: org.hibernate.dialect.H2Dialect

## API Endpoints

The API provides the following endpoints:

### Get All Fruits

```
GET /fruits
```

Returns a list of all fruits in the database.

### Get Fruit by ID

```
GET /fruits/{id}
```

Returns a single fruit with the specified ID.

### Create Fruit

```
POST /fruits
```

Creates a new fruit. The request body should be a JSON object with the following structure:

```json
{
  "name": "Apple",
  "quantity": 10
}
```

### Update Fruit

```
PATCH /fruits/{id}
```

Updates an existing fruit with the specified ID. The request body should be a JSON object with the fields you want to update:

```json
{
  "name": "Updated Apple",
  "quantity": 20
}
```

### Delete Fruit

**Note**: The delete functionality is implemented in the service layer (`DeleteFruitByIdService`), but there is no corresponding endpoint in the controller. To add this functionality, you would need to add a DELETE endpoint to the `FruitsController`.

## Data Model

### Fruit

- **id** (long): The primary key, auto-generated
- **name** (String): The name of the fruit
- **quantity** (int): The quantity of the fruit

## Error Handling

The application includes custom exception handling for various error scenarios, such as when a fruit does not exist or cannot be found.

## Running the Application

To run the application, use the following command:

```bash
./gradlew bootRun
```

The API will be available at `http://localhost:8080`.
