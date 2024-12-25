# JSP-Hibernate
# Hibernate Simple CRUD Operation Project

## Project Overview
This project demonstrates a simple CRUD (Create, Read, Update, Delete) operation using Hibernate. Hibernate is an Object-Relational Mapping (ORM) tool for Java that simplifies database interactions.

---

## Folder Structure

```
/hibernate_simplecrudopration
    └── src
        └── main
            ├── java
            │   └── com
            │       └── example
            │           └── hibernatecrud
            │               ├── entity
            │               │   └── [Entity Classes]
            │               ├── dao
            │               │   └── [DAO Classes]
            │               └── main
            │                   └── [Main Application]
            └── resources
                └── META-INF
                    └── persistence.xml
```

### Key Components:
1. **Entity Classes**: Represent database tables.
2. **DAO (Data Access Object) Classes**: Contain CRUD operations.
3. **Main Application**: Entry point of the application.
4. **persistence.xml**: Configuration file for Hibernate.

---

## Persistence.xml File
The `persistence.xml` file is located at:
```
/hibernate_simplecrudopration/src/main/resources/META-INF/persistence.xml
```

### Code:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<persistence version="3.0" xmlns="https://jakarta.ee/xml/ns/persistence"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="https://jakarta.ee/xml/ns/persistence 
             https://jakarta.ee/xml/ns/persistence/persistence_3_0.xsd">

  <persistence-unit name="hibernate-a5"> 
    <properties>
      <property name="jakarta.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver" />
      <property name="jakarta.persistence.jdbc.url"    value="jdbc:mysql://localhost:3306/DB_NAME" />
      <property name="jakarta.persistence.jdbc.user"   value="root" />
      <property name="jakarta.persistence.jdbc.password" value="root" />
      <property name="jakarta.persistence.schema-generation.database.action" value="update" />
      <property name="hibernate.dialect"    value="org.hibernate.dialect.MySQLDialect" />
      <property name="hibernate.show_sql"   value="true" />
      <property name="hibernate.format_sql" value="true" />
    </properties>
  </persistence-unit>
</persistence>
```

### Explanation:
- **`persistence-unit`**: Defines the configuration for the persistence context.
- **`jakarta.persistence.jdbc.driver`**: Specifies the JDBC driver for MySQL.
- **`jakarta.persistence.jdbc.url`**: Specifies the database URL.
- **`jakarta.persistence.jdbc.user` and `jakarta.persistence.jdbc.password`**: Set database credentials.
- **`hibernate.dialect`**: Specifies the Hibernate dialect for MySQL.
- **`hibernate.show_sql` and `hibernate.format_sql`**: Enable and format SQL logging.

---

## How It Works

1. **Setup the Project**
   - Add Hibernate and MySQL dependencies to your `pom.xml` or build.gradle.
   - Define your database connection details in `persistence.xml`.

2. **Create Entity Classes**
   - Define entity classes annotated with `@Entity`.
   - Map fields to database columns using annotations like `@Column` and `@Id`.

3. **Write DAO Classes**
   - Implement CRUD operations using the `EntityManager`.

4. **Run Main Application**
   - Bootstrap the persistence context using `Persistence.createEntityManagerFactory`.
   - Perform CRUD operations through the DAO layer.

---

## Example Usage
### Main Application:
```java
import com.example.hibernatecrud.dao.ExampleDAO;
import com.example.hibernatecrud.entity.ExampleEntity;

public class Main {
    public static void main(String[] args) {
        ExampleDAO dao = new ExampleDAO();

        // Create
        ExampleEntity entity = new ExampleEntity();
        entity.setName("Example Name");
        dao.create(entity);

        // Read
        ExampleEntity retrieved = dao.read(entity.getId());
        System.out.println(retrieved);

        // Update
        retrieved.setName("Updated Name");
        dao.update(retrieved);

        // Delete
        dao.delete(retrieved.getId());
    }
}
```

---

## Notes
- Ensure MySQL is running and the database `DB_NAME` exists.
- Replace the database credentials as per your environment.
- Follow best practices for exception handling and resource management.

---

## Dependencies 
## projectlombok
```
<dependency>
		<groupId>org.projectlombok</groupId>
		<artifactId>lombok</artifactId>
		<version>1.18.36</version>
		<scope>provided</scope>
</dependency>
```
 ## mysql-connector
```
<!-- https://mvnrepository.com/artifact/com.mysql/mysql-connector-j -->
	<dependency>
		<groupId>com.mysql</groupId>
      		<artifactId>mysql-connector-j</artifactId>
      		<version>8.4.0</version>
	</dependency>
```

## hibernate-core
```
<!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-core -->
	<dependency>
	    <groupId>org.hibernate</groupId>
	    <artifactId>hibernate-core</artifactId>
	    <version>6.0.0.Final</version>
	</dependency>
```
### jakarta.servlet-api
```
 <!-- https://mvnrepository.com/artifact/jakarta.servlet/jakarta.servlet-api -->
	<dependency>
	    <groupId>jakarta.servlet</groupId>
	    <artifactId>jakarta.servlet-api</artifactId>
	    <version>6.0.0</version>
	    <scope>provided</scope>
	</dependency>

```

## End
