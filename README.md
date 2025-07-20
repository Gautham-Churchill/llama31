# llama31

A demo project built with Spring Boot, showcasing integration with Spring AI and the Ollama model. This application serves as a starting point for building AI-powered web services using Java.

## Tech Stack
- Java 21
- Spring Boot 3.4.7
- Spring AI (Ollama model)
- Maven

## Getting Started

### Prerequisites
- Java 21 or higher
- Maven
- Ollama model installed and running

### Clone the Repository
```
git clone https://github.com/Gautham-Churchill/llama31.git
cd llama31
```

### Build the Project
```
./mvnw clean install
```

### Run the Application
```
./mvnw spring-boot:run
```

### Command to run Ollama model
In this project, we are using the `llama3.1:8b` model from Ollama. To run this model, ensure you have Ollama installed and then execute the following command in your terminal:
```
ollama run llama3.1:8b
```

The application will start on the default port (usually 8080). You can access it via your browser or API client.

### API Endpoints
Test the end points using httpie or curl.
Example using httpie:
```bash
http :8080/joke - This endpoint returns a random dad joke about computers.
http POST :8080/joke message={Ask a question} - This endpoint allows you to ask a question and get a response from the Ollama model.
```
#### Example Request
```bash
http POST :8080/joke message="Capital of France?"
```

## Additional Information
- Configuration files are located in `src/main/resources`.
- Main application entry point: `src/main/java/dev/gautham/llama31/Application.java`

