# Ansible Collection - `pumphouse_p.cicd`

## Description

This collection containers various roles that are intended to act as
steps in an application build and release pipeline.

## Requirements

- `amazon.aws`
- `ansible.builtin`

## Variables

There are two scopes for variables that can be set within this collection:

1. Collection-scoped
2. Role-scoped

### Collection-Scoped

In a build and release pipeline, there are some parameters that will need to be used
by multiple steps in the pipeline. These are collection-scoped variables in this content,
meaning you can set them once in a vars file or directly in your playbook, and the values
will be used by other roles included in this collection where appropriate. The table
below describes the available variables.

|    Variable Name     | Default | Required | Type |                           Description                           |
|:--------------------:|:-------:|:--------:|:----:|:---------------------------------------------------------------:|
| `cicd_workspace_dir` |   ""    |   yes    | str  |             Base directory where build files exist              |
|  `cicd_output_file`  |   ""    |   yes    | str  | Filename relative to `cicd_workspace_dir` that contains release |

### Role-Scoped

The second scope for variables are set at the role-level. These role-scoped variables
are specific to the role and it's internal configuration/functionality. Review the
role-specific README to get more information about what variables are available.

## Dependencies

None.

## License

GPL

## Author Information

Devin Parrish ([GitHub](https://github.com/pumphouse-p))