# Terraform plan destroy action

This is a composite action made for `Terraform plan -destroy` command to see all the resources present in the Infrastructure that are going to be destroyed. This command is nessessary to see the resources before they are destroyed and choose accroding to your need.

The way this action works is the following:

1. Workflow comes to the `Terraform plan destroy` action.
1. `Terraform plan destroy` will go to the directory where the terraform configuration files are present.
1. If the terraform configuration is configured correctly the action will perform the `Terraform plan destroy` command of the files present and display the resources to be deleted.

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
  - uses: sparshbaurasi/github-shared-cp/TerraformPlanDestroy@main
    with:
     DIRECTORY: ${{github.event.inputs.DIRECTORY_NAME}}
```

## Limitations

* One should always include state file management code to there terraform configuration for ignore any unintentional deletion or creation of resources.
