# Java-app

A simple Java application built with Maven.

## Prerequisites

- Java 8 or higher
- Maven 3.6 or higher

## Building the Application

To compile the application, run:

```bash
mvn compile
```

## Running the Application

To run the application locally, use:

```bash
mvn exec:java
```

This will start a web server on port 8080 (or the PORT environment variable) and respond with "Hello, World!" at the root path.

To run the packaged JAR:

```bash
java -jar target/java-app-1.0-SNAPSHOT-jar-with-dependencies.jar
```

## CI/CD with GitHub Actions

This project includes a GitHub Actions workflow for continuous integration and deployment to Azure App Service.

### Setup

1. Create an Azure App Service with Java runtime stack.
2. Obtain the publish profile from the Azure portal.
3. Add the publish profile as a secret named `AZURE_APP_SERVICE_PUBLISH_PROFILE` in your GitHub repository.
4. Update the `app-name` in `.github/workflows/ci-cd.yml` to match your App Service name.

### Deployment

The workflow will automatically build and deploy on pushes to the `main` branch.

### Setup Instructions

1. **Create an Azure App Service:**
   - Go to the Azure Portal
   - Create a new App Service (Web App)
   - Choose Java 8 as the runtime stack
   - Note down the App Service name

2. **Get the Publish Profile:**
   - In the Azure Portal, go to your App Service
   - Click on "Get publish profile"
   - Download the `.PublishSettings` file

3. **Add Secrets to GitHub Repository:**
   - Go to your GitHub repository
   - Navigate to Settings > Secrets and variables > Actions
   - Add a new repository secret named `AZURE_APP_SERVICE_PUBLISH_PROFILE`
   - Copy the entire content of the `.PublishSettings` file and paste it as the secret value

4. **Update the Workflow:**
   - Edit `.github/workflows/ci-cd.yml`
   - Replace `'your-app-service-name'` with your actual App Service name

5. **Push to Main Branch:**
   - Commit and push your changes to the `main` branch
   - The workflow will automatically trigger and deploy to Azure

### Manual Deployment

You can also trigger the workflow manually from the Actions tab in GitHub.