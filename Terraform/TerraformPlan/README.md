# Terraform plan action

This is a composite action made for `Terraform plan` command to planiatize any Infrastructure. This command is nessessary before for building any infrastructrue and without running this command we cannot build any infrastructure.

The way this action works is the following:

1. Workflow comes to the `Terraform plan` action.
1. `Terraform plan` will go to the directory where the terraform configuration files are present.
1. If the terraform configuration is configured correctly the action will perform the `Terraform plan` command of the files present and display the resources to be provisioned.

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
  - uses: sparshbaurasi/github-shared-cp/Terraformplan@main
    with:
     DIRECTORY: ${{github.event.inputs.DIRECTORY_NAME}}
```

## Limitations

* One should always include state file management code to there terraform configuration for ignore any unintentional deletion or creation of resources.