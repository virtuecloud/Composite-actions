# Terraform Apply action

This is a composite action made for `Terraform apply` command to build any Infrastructure. This is a very common command for the deployment of an infrastructure on any platform that are present under terraform registry.

The way this action works is the following:

1. Workflow comes to the `Terraform apply` action.
1. `Terraform apply` will go to the directory wwhere the terraform configuration files are present.
1. If the terraform configuration is configured correctly the action will perform the `Terraform apply ` command of the same.

## inputs

```yaml
inputs:
  DIRECTORY:
    description: 'Directory name for terraform source configuration'
    required: true
```

## Usage

```yaml
steps:
  - uses: sparshbaurasi/github-shared-cp/TerraformApply@main
    with:
     DIRECTORY: ${{github.event.inputs.DIRECTORY_NAME}}
```

## Limitations

* While the workflow will run successfully if the configuration is provisioned correctly. There is high chance that the configuration code may be changed between the `terraform init` command and this action. So it is advised the one should always include a state file management configuration to there terraform configuration file.