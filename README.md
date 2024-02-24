# 3TierGitOpsOnGCP
A GitOps-driven framework for deploying a 3-tier applications on Google Cloud Platform, featuring automated workflows, secure secret management, and Infrastructure as Code for efficient cloud-native development.

## Prerequisites

Ensure you already have access to your project on Google Cloud Plateform.
You will need to have the permission to use Compute Instance, Network and Google Cloud Storage for Terraform backend.
You'll probably will need to be a domain name administrator to make the SSL certificate work as intended. 

## Todo list

In this section, you'll find the roadmap of this project. So if you want to contribute, this can be a good section to read. 
- Writing documentation
- Secret management

## Project Structure

This deployment project is organized around 3 axes :
- `terraform /` folder will be your first landingzone to initiate your backend and create your infrastructure
  - A `docker-compose.yml` allow you to launch terraform in a container for a better version management
  - You'll have to specify the backend.tfvars depending on the environment
  - Project still has to evolve to workspaces or terragrunt
- `ansible /` folder is used to run any ansible related configuration management task
  - Ansible and Python version are managend through Poetry virtual env 
- `docker-compose.yml` is the 3 Tier application stack we want to deploy to GCP

Each axes is documented on it's own folder.

## Contributing

To contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch: `git checkout -b branch_name`.
3. Make your changes and commit them: `git commit -am 'commit message'`.
4. Push to the original branch: `git push origin project_name/branch_name`.
5. Create the pull request.

Alternatively, see the GitHub documentation on [creating a pull request](https://help.github.com/articles/creating-a-pull-request/).

## Help

If you encounter any problems, please file an issue along with a detailed description.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
The MIT License is a permissive license that is short and to the point. It lets people do anything they want with your code as long as they provide attribution back to you and don’t hold you liable.
Feel free to use, modify, and distribute this software for personal and commercial purposes under these conditions.
