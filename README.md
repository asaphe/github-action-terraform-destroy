# github-action-terraform-destroy

A composite GitHub Action for running Terraform destroy with workspace support and loop mode over tfvars files.

## Usage

### Single Workspace

```yaml
- uses: asaphe/github-action-terraform-destroy@v1
  with:
    working-directory: devops/terraform/my-module
    workspace: staging
    var-file: vars/staging.tfvars
```

### Destroy Plan Only (Dry Run)

```yaml
- uses: asaphe/github-action-terraform-destroy@v1
  with:
    working-directory: devops/terraform/my-module
    workspace: staging
    var-file: vars/staging.tfvars
    plan-only: "true"
```

### Loop Over tfvars Directory

```yaml
- uses: asaphe/github-action-terraform-destroy@v1
  with:
    working-directory: devops/terraform/my-module
    workspace: staging
    var-file: vars/
    loop-over-tfvars: "true"
```

## Inputs

| Name | Description | Required | Default |
|------|-------------|----------|---------|
| `working-directory` | Directory to run Terraform in | Yes | - |
| `workspace` | Terraform workspace name (or base name for loop) | Yes | - |
| `var-file` | Path to tfvars file or directory | No | - |
| `parallelism` | Parallelism for destroy | No | - |
| `loop-over-tfvars` | If true, loop over all tfvars files | No | `false` |
| `plan-only` | If true, only create a destroy plan | No | `false` |

## Features

- Graceful workspace handling: skips destroy if workspace doesn't exist
- Loop mode: iterates over all `.tfvars` files in a directory
- Plan-only mode for safe previews with `plan -destroy`

## License

Apache 2.0 - See [LICENSE](LICENSE) for details.
