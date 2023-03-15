# Terraform Init action

This is a composite action made for `Terraform init` command to initiatize any Infrastructure. This command is nessessary before for building any infrastructrue and without running this command we cannot build any infrastructure.

The way this action works is the following:

1. Workflow comes to the `Terraform init` action.
1. `Terraform init` will go to the directory where the terraform configuration files are present.
1. Then there is an addition command present in this composite action which is `terraform workspace new` and `terraform workspace select`
1. What `terraform workspace new` will do is to take an input as environment and checks if the environment is present and if not then it creates the one specified
1. `terraform workspace select` command will select the workspace which is specified in the inputs
1. If the terraform configuration is configured correctly the action will perform the `Terraform init` command of the same.

## inputs
```yaml
inputs:
  DIRECTORY:
    description: 'Directory name for terraform source configuration'
    required: true
  ENVIRONMENT_NAME:
    description: 'Environment name'
    required: true
```

## Usage

```yaml
steps:
  - uses: sparshbaurasi/github-shared-cp/Terraforminit@main
    with:
     DIRECTORY: ${{github.event.inputs.DIRECTORY_NAME}}
     ENVIRONMENT: ${{github.event.inputs.ENVIRONMENT_NAME}}
```

## Limitations

* One should always include state file management code to there terraform configuration for ignore any unintentional deletion or creation of resources.