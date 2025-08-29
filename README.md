Here’s the **README.md** file content wrapped for direct use. You can copy-paste it into a file named `README.md` at the root of your repo.

---

```markdown
# Spring SQL Task – Automated Webhook Submission

## Overview

This Spring Boot application automates your assignment workflow:

- On startup, sends a POST request to generate a webhook and accessToken.
- Determines which SQL question to answer based on your `regNo`.
- Submits your final SQL query to the provided webhook URL using JWT authorization.

---

## Project Structure

```

spring-sql-task/
├── src/main/java/com/example/springsqltask/
│    ├── SpringSqlTaskApplication.java   # Main class (runs on startup)
│    ├── client/
│    │     └── WebhookClient.java        # Makes POST requests to API
│    ├── model/
│    │     └── WebhookResponse.java      # Parses webhook and token response
│    └── service/
│          └── SqlSolverService.java     # Picks SQL query based on regNo
├── src/main/resources/
│    └── application.properties          # (Empty by default)
├── pom.xml                              # Maven dependencies
├── mvnw, mvnw\.cmd                       # Maven wrapper scripts
├── HELP.md                              # Assignment instructions
└── README.md                            # This documentation

````

---

## Prerequisites

- **Java JDK 17+**
- No need to install Maven—this project includes Maven Wrapper (`mvnw` / `mvnw.cmd`).

---

## Setup & Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/KavinKarthik18/22brs1049-bajaj-submission.git
   cd 22brs1049-bajaj-submission
````

2. Verify Java installation:

   ```bash
   java -version
   ```

3. Build the project using Maven Wrapper:

   **On Windows (PowerShell):**

   ```powershell
   & ".\mvnw" clean install
   & ".\mvnw" spring-boot:run
   ```

   **On Linux/macOS:**

   ```bash
   ./mvnw clean install
   ./mvnw spring-boot:run
   ```

---

## How It Works

1. On startup, sends a POST to:

   ```
   https://bfhldevapigw.healthrx.co.in/hiring/generateWebhook/JAVA
   ```

   with:

   ```json
   {
     "name": "<Your Name>",
     "regNo": "<Your RegNo>",
     "email": "<Your Email>"
   }
   ```

2. Receives `webhook` URL and `accessToken`.

3. Based on your `regNo`, chooses the correct SQL question (odd/even logic).

4. You solve the SQL, update `SqlSolverService.java` with your final query.

5. App submits the solution:

   ```
   POST <webhook>
   Headers:
     Authorization: <accessToken>
     Content-Type: application/json

   Body:
   {
     "finalQuery": "<Your SQL Query>"
   }
   ```

---

## Example Console Output

```
Webhook: https://bfhldevapigw.healthrx.co.in/hiring/testWebhook/JAVA
Token: eyJhbGciOiJ...
Question link: https://drive.google.com/...
Submitting final SQL query...
Response: success
```

---

## Build JAR (Optional)

If you need a standalone JAR for submission:

```bash
& ".\mvnw" clean package   # (Windows PowerShell)
./mvnw clean package       # (Linux/macOS)
java -jar target/*.jar
```

---

## Submission Checklist

* GitHub repository link:

  ```
  https://github.com/KavinKarthik18/22brs1049-bajaj-submission.git
  ```

* Include:

  * All source code
  * `target/` folder containing the generated JAR
  * A downloadable link to the JAR (e.g., via GitHub releases or Google Drive)

---

## Notes

* Make sure to replace placeholders (`<Your Name>`, `<Your RegNo>`, etc.) in `WebhookClient.java`.
* Use the Maven Wrapper (`mvnw`) script to build and run—paths with spaces require using `& ".\mvnw"` syntax on PowerShell.
* The app automatically performs the full workflow—no manual HTTP calls required after setting up.

---

## Good Luck!

```

---

Do you also want me to create and give you the **exact `pom.xml`** so your repo is fully ready-to-run without missing dependencies?
```
