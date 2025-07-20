# Copilot Instructions for llama31

## Project Overview
- **llama31** is a Spring Boot (Java 21) web service integrating Spring AI and the Ollama model (`llama3.1:8b`).
- Main entry point: `src/main/java/dev/gautham/llama31/Application.java`.
- REST API controller: `src/main/java/dev/gautham/llama31/ChatController.java` exposes `/joke` endpoints for interacting with the AI model.
- Configuration: `src/main/resources/application.properties` and Maven `pom.xml`.

## Architecture & Data Flow
- The application is a stateless REST API.
- `ChatController` uses `ChatClient` (from Spring AI) to send prompts to the Ollama model and return responses.
- All requests to `/joke` (GET for a joke, POST for custom prompt) are routed through the AI model.
- No database or persistent storage is present.

## Developer Workflows
- **Build:** `./mvnw clean install`
- **Run:** `./mvnw spring-boot:run`
- **Test:** `./mvnw test` (JUnit, see `Llama31ApplicationTests.java`)
- **Ollama Model:** Ensure Ollama is installed and running. Start with: `ollama run llama3.1:8b`
- **API Testing:** Use `httpie` or `curl`:
  - `http :8080/joke` (GET)
  - `http POST :8080/joke message="Your question"` (POST)

## Conventions & Patterns
- All REST endpoints are under `/joke`.
- Controller methods use direct prompt-to-response mapping via `ChatClient`.
- No custom error handling or DTOs; responses are plain strings.
- Configuration values (model name, etc.) are set in `application.properties`.
- Maven wrapper (`mvnw`, `mvnw.cmd`) is used for builds; do not require global Maven install.

## Integration Points
- **Spring AI:** Integrated via `spring-ai-starter-model-ollama` dependency.
- **Ollama:** External process; must be running for API to function.
- No other external services or databases.

## Key Files & Directories
- `src/main/java/dev/gautham/llama31/Application.java` (main class)
- `src/main/java/dev/gautham/llama31/ChatController.java` (API logic)
- `src/main/resources/application.properties` (config)
- `pom.xml` (dependencies)
- `README.md` (usage and workflow)

## Example: Adding a New Endpoint
- Add a new method to `ChatController` with appropriate `@GetMapping` or `@PostMapping`.
- Use `chatClient.prompt().user("your prompt").call().content()` to interact with the model.

## Coding Guidelines
Follow these guidelines when writing & reviewing code for the project:
- Follow SOLID principles for class design.
- Use Java 21 features where appropriate (e.g., switch expressions, records).
- Follow standard Java conventions (camelCase for methods, PascalCase for classes).
- Use `@RestController` for API controllers.
- Use constructor injection for dependencies (e.g., `ChatClient`).
- Follow SonarQube rules for code quality (e.g., no unused imports, proper exception handling).
- Use RestClient for HTTP requests in tests.
- Use JUnit & AssertJ for tests; see `Llama31ApplicationTests.java` for examples.

---
For more details, see `README.md` and referenced source files. If unclear, ask for clarification or examples from the user.
