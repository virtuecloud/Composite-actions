# Terraform Destroy action

This is a composite action made for `Terraform destroy` command to Destroy any Infrastructure. This is a very common command to destroy any infrastructure which was provisioned through terraform.

The way this action works is the following:

1. Workflow comes to the `Terraform destroy` action.
1. `Terraform destroy` will go to the directory wwhere the terraform configuration files are present.
1. If the terraform configuration is configured correctly the action will perform the `Terraform destroy` command of the same.

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
  - uses: sparshbaurasi/github-shared-cp/TerraformDestroy@main
    with:
     DIRECTORY: ${{github.event.inputs.DIRECTORY_NAME}}
```

## Limitations

* Its is advised to run `terraform init` action before this action as it will reference the state file and the workspace for terraform to delete only those resources which are present under a certain workspace.