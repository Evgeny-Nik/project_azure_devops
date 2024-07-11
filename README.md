# Azure DevOps CI/CD Project for HelloWorldApp

## Source Code
This project contains a simple C# application.
```C#
Console.WriteLine("Hello, World!");
```

## Azure DevOps CI/CD Stages
This Azure DevOps pipeline automates the process of building, analyzing, and packaging a .NET application, and publishing the package to a NuGet repository.

### Trigger:
The pipeline is triggered on Push events to the `master` branch.
```yaml
trigger:
- master
```
### Job Steps

- **Checkout**: Checks out the repository and cleans the workspace.
- **Prepare SonarQube**: Prepares SonarQube for code analysis.
- **Build**: Builds the .NET application.
- **Analyze**: Runs code analysis with SonarQube.
- **Publish Quality Gate**: Publishes the quality gate results.
- **Set Version**: Sets the version number for the NuGet package.
- **Display Version**: Displays the version number.
- **Create NuGet Package**: Packages the application as a NuGet package.
- **Tag Build**: Tags the build with the branch and version.
- **Publish NuGet Package**: Publishes the NuGet package to the repository.

## Versioning Logic
The project adheres to semantic versioning (Major.Minor.BuildId) to ensure a structured and predictable versioning system.

## Plugin Used

#### Azure DevOps Tasks:
- ***SonarQubePrepare@5*** - Prepares the project for SonarQube analysis.
- ***SonarQubeAnalyze@5*** - Analyzes the project with SonarQube.
- ***SonarQubePublish@5*** - Publishes the quality gate results.
- ***artifactstager@1*** - Tags the build.

## Reproducing the Project

To reproduce this project, follow these steps:

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/Evgeny-Nik/azure-devops-pipeline.git
    cd azure-devops-pipeline
    ```

2. **Set Up Azure DevOps Pipeline**:
   - Navigate to your Azure DevOps project.
   - Go to Pipelines > New Pipeline.
   - Select "GitHub Git" as the source.
   - Select your repository.
   - Choose one of the following
     - "Starter Pipeline" and replace its content with the provided pipeline YAML.
     - "Existing Azure Pipelines YAML file" and set branch and path of the YAML file.

3. **Configure SonarQube**:
   - Make sure you have a SonarQube instance running.
   - Create a project in SonarQube and note the `projectKey`.
   - Set up a service connection in Azure DevOps for SonarQube:
     - Navigate to Project Settings > Service Connections.
     - Click on "New service connection" and select "SonarQube".
     - Enter your SonarQube server URL, authentication token, and a connection name (e.g., `azure_devops_pipeline_connection_master`).
     - Optionally, set up custom notifications in Project Settings > Notifications.

4. **Create NuGet Feed**:
   - Set up a NuGet feed in Azure DevOps or use an existing one.
   - Note the source URL for the NuGet feed.

5. **Run the Pipeline**:
   - Commit and push your changes.
   - The pipeline will trigger on the `master` branch push.


## Links

- [Azure DevOps Documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started-yaml?view=azure-devops)
