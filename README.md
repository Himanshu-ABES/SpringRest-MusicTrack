# Spring Boot Music Track REST API (20MarchAssignment-2)

This repository contains a Spring Boot REST API for managing music tracks, created as an assignment. It provides CRUD operations to create, read, and search tracks.

## Technologies Used
* **Java** 
* **Spring Boot** (Web, Data JPA)
* **PostgreSQL** Database
* **Maven**

## Project Structure
* `com.cg.entity.Track`: The JPA Entity mapping to the `abes_track` table in the database.
* `com.cg.repo.TrackRepository`: Spring Data JPA repository for database operations.
* `com.cg.web.TrackController`: The REST controller defining the API endpoints.

## Database Configuration
The application connects to a local PostgreSQL database. Ensure you have a database named `abesdb2` running on `localhost:5432`.

**Default Credentials:**
* Username: `postgres`
* Password: `12345678`

The database schema is automatically updated via Hibernate (`spring.jpa.hibernate.ddl-auto=update`).

## Entity Details: `Track`
* `id` (Long, Primary Key)
* `title` (String, mapped to `track_title`)
* `albumName` (String, mapped to `album_name`)
* `releaseDate` (LocalDate, mapped to `release_dt`)

## API Endpoints

All endpoints have the base path `/music`.

| HTTP Method | Endpoint | Description |
|---|---|---|
| `POST` | `/music/tracks` | Create a new music track. Expects a JSON payload. |
| `GET` | `/music/tracks` | Retrieve a list of all tracks. |
| `GET` | `/music/tracks/{id}` | Retrieve a specific track by its ID. |
| `GET` | `/music/tracks/search?title={title}` | Search and retrieve tracks by their title. |

### Example Payload (`POST /music/tracks`)
```json
{
  "title": "Bohemian Rhapsody",
  "albumName": "A Night at the Opera",
  "releaseDate": "1975-10-31"
}
```

## How to Run
1. Start your local PostgreSQL server with the required credentials.
2. Navigate to the `SpringBootRestTest` directory.
3. Build and run the project using the Maven Wrapper:
   ```bash
   cd SpringBootRestTest
   ./mvnw spring-boot:run
   ```
4. The server will start on port `8080` by default. You can test the endpoints using tools like Postman or cURL.