# Terraform deployment on GCP

This folder contains Terraform code to manage infrastructure across multiple projects within GCP efficiently. The infrastructure code is organized to support modular and scalable deployments.

## Folder Structure

- `data.tf`: Contains data source configurations that Terraform uses to fetch and compute data for other resources.
- `environments/`: Directory containing environment-specific configurations. Each environment sub-directory has its `backend.tfvars` file to configure Terraform backends appropriately.
  - `preprod/`, `prod/`, `staging/`: Each environment directory contains specific backend configurations for that environment.
- `main.tf`: The primary entry point for Terraform configurations in this project.
- `modules/`: Contains modular Terraform configurations for different types of resources.
  - `compute/` and `network/`: Specific modules for compute and network resources, respectively, each with its own set of Terraform files (`main.tf`, `variables.tf`, `outputs.tf`, and optionally `data.tf`).
- `outputs.tf`: Defines output values that other modules or Terraform itself might use.
- `provider.tf`: Configures the Terraform provider(s) used in the project.
- `variables.tf`: Declares variables used across the Terraform configurations.

This structured approach enhances the maintainability, scalability, and clarity of the Terraform project, facilitating better infrastructure management across multiple GCP environments.

## Prerequisites in GCP

1. **Bucket Creation for Terraform Backend:**
   - Create a GCP bucket in Cloud Storage to store Terraform state files. This ensures state is shared and locked across team members, enhancing state management and collaboration.
   - Don't forget to enable encryption by providing your generated encryption key.
   - Don't forget to enable versionning

```sh
gsutil mb -p [PROJECT_ID] -c STANDARD -l [LOCATION] -b on gs://[BUCKET_NAME]
```

2. **Enable Cloud Resource Manager API:**
- The Cloud Resource Manager API must be enabled to allow Terraform to interact with GCP resources.

## Using Docker-Compose

We use Docker-compose to run Terraform within a container to ensure a consistent and isolated environment for infrastructure deployment. This approach mitigates issues related to varying Terraform versions and dependency management across different machines and environments.

### Why Docker-Compose?

- **Consistency:** Docker containers provide a consistent environment across different development and CI/CD pipelines, reducing "works on my machine" problems.
- **Isolation:** Running Terraform inside a container isolates the Terraform execution, minimizing conflicts with system-level dependencies and ensuring that Terraform runs with its required dependencies and versions.
- **Portability:** Using Docker-compose allows the Terraform setup to be portable and easily replicated across different machines without the need for complex environment setups.

### Docker-Compose Setup

- `docker-compose.yml`: Specifies how to build and run the containerized Terraform environment.

```sh

```

## Conclusion

By following this structure and setup, contributors can efficiently use and develop their GCP resources across multiple pojects.
This setup is not mandatory and can be improve but it ensure Terraform version isolation on a container for people who work with multiple projects.

