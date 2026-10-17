# Internship & Job Application Tracker

A beginner-friendly full-stack portfolio project to organize internship and job applications. Built with **Java 17, Spring Boot, Spring Data JPA, H2 SQL, HTML, CSS, and JavaScript**.

## Features
- Add, view, edit, and delete applications (CRUD).
- Track Saved, Applied, Assessment, Interview, Offer, Rejected, and Withdrawn statuses.
- Store company, role, type, application date, follow-up date, posting URL, and notes.
- Search by company, role, or type; filter by status.
- Dashboard summary cards for totals, in-progress applications, interviews, and offers.
- Responsive desktop/mobile interface.
- Persistent file-based H2 SQL database; no separate database install required.
- REST API with basic field validation.

## Tech stack
Java 17 · Spring Boot 3.4.5 · Spring Web · Spring Data JPA/Hibernate · H2 Database · MySQL connector · HTML/CSS/JavaScript · Maven.

## Requirements
Install JDK 17+ and Maven 3.6.3+ (or use an IDE with Maven support). Check with `java -version` and `mvn -version`.

## Run the project
1. Extract or clone the repository.
2. Open the folder containing `pom.xml` in IntelliJ IDEA, Eclipse, or VS Code with Java extensions.
3. Allow Maven to download dependencies.
4. Run `TrackerApplication.java`, or open a terminal in the project folder and run:

```bash
mvn spring-boot:run
```

5. Open **http://localhost:8080**.

The database is created in `data/` and persists between restarts. The `data/` folder is excluded from Git because it can contain personal information.

### Run tests
```bash
mvn test
```

### Optional H2 console
Open `http://localhost:8080/h2-console` while the application is running:
- JDBC URL: `jdbc:h2:file:./data/application-tracker;DB_CLOSE_ON_EXIT=FALSE`
- Username: `sa`
- Password: leave blank

The H2 console is for local development only; do not expose it publicly.

## REST API
Base path: `/api/applications`

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/applications` | List applications |
| GET | `/api/applications?status=INTERVIEW` | Filter by status |
| GET | `/api/applications?search=google` | Search company/role/type |
| GET | `/api/applications/{id}` | Get one application |
| GET | `/api/applications/statuses` | List valid statuses |
| POST | `/api/applications` | Create application |
| PUT | `/api/applications/{id}` | Update application |
| DELETE | `/api/applications/{id}` | Delete application |

Example JSON for POST:

```json
{
  "company": "Example Technologies",
  "roleTitle": "Software Developer Intern",
  "applicationType": "Internship",
  "jobUrl": "https://example.com/careers",
  "status": "APPLIED",
  "appliedDate": "2026-10-17",
  "followUpDate": "2026-10-24",
  "notes": "Prepare Java collections for the interview."
}
```

Valid statuses: `SAVED`, `APPLIED`, `ASSESSMENT`, `INTERVIEW`, `OFFER`, `REJECTED`, `WITHDRAWN`.

## Optional: switch to MySQL
H2 is the default so beginners can run this without installing MySQL. To switch:
1. Create a database: `CREATE DATABASE career_tracker;`
2. Set environment variables (PowerShell example; use your own credentials):

```powershell
$env:SPRING_DATASOURCE_URL="jdbc:mysql://localhost:3306/career_tracker"
$env:SPRING_DATASOURCE_USERNAME="your_mysql_username"
$env:SPRING_DATASOURCE_PASSWORD="your_mysql_password"
$env:SPRING_DATASOURCE_DRIVER_CLASS_NAME="com.mysql.cj.jdbc.Driver"
```

3. In `application.properties`, remove/comment the H2 datasource URL, H2 driver, and H2 console settings. Keep `spring.jpa.hibernate.ddl-auto=update`.
4. Run `mvn spring-boot:run` in that same terminal session.

Never commit real passwords, `.env` files, or personal application records to a public repository.

## GitHub upload (without Git commands)
1. Extract the ZIP.
2. Create a repository named `internship-job-application-tracker` at [GitHub](https://github.com/new).
3. In the new repository choose **Add file → Upload files**.
4. Upload the extracted project contents: `pom.xml`, `src/`, `.gitignore`, and `README.md`. Do not upload `target/` or private `data/` files.
5. Use commit message `Add Internship and Job Application Tracker`, then click **Commit changes**.

## GitHub About description
A full-stack Internship & Job Application Tracker built with Java, Spring Boot, Spring Data JPA, H2 SQL, and a responsive HTML/CSS/JavaScript dashboard. Track application status, deadlines, notes, and follow-ups.

Suggested topics: `java`, `spring-boot`, `spring-data-jpa`, `sql`, `h2-database`, `job-tracker`, `internship-tracker`, `rest-api`.

## Project structure
```text
internship-job-application-tracker/
├── pom.xml
├── README.md
├── .gitignore
└── src/
    ├── main/java/com/jasmin/tracker/
    │   ├── TrackerApplication.java
    │   ├── controller/JobApplicationController.java
    │   ├── model/ApplicationStatus.java
    │   ├── model/JobApplication.java
    │   └── repository/JobApplicationRepository.java
    ├── main/resources/
    │   ├── application.properties
    │   └── static/{index.html,styles.css,app.js}
    └── test/java/com/jasmin/tracker/TrackerApplicationTests.java
```

## Future improvements
Login and user accounts, calendar view, CSV export, email reminders, and deployment.

## License
For learning and portfolio use. Add a license file if you want to specify reuse terms.
