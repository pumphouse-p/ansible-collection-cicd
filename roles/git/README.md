# README for `cicd.git`

## Description

Installs git and clones a repo.

## Requirements

- `ansible.builtin`

## Role Variables

### Collection Scoped Configuration

|    Variable Name     | Default | Required | Type |                           Description                           |
|:--------------------:|:-------:|:--------:|:----:|:---------------------------------------------------------------:|
| `cicd_workspace_dir` |   ""    |   yes    | str  |             Base directory where build files exist              |
|  `cicd_output_file`  |   ""    |   yes    | str  | Filename relative to `cicd_workspace_dir` that contains release |

### General Configuration

|     Variable Name      | Default  | Required | Type |                        Description                        |
|:----------------------:|:--------:|:--------:|:----:|:---------------------------------------------------------:|
|       `git_src`        |    ""    |   yes    | str  | git, SSH, or HTTPS protocol address of the git repository |
|       `git_dest`       |    ""    |   yes    | str  |     Path to where the repository should be cloned to.     |
|     `git_version`      |  `main`  |    no    | str  |   Version of the repository to clone (branch, tag, SHA)   |
|      `git_force`       |  `true`  |    no    | bool |    Discard modified files in the `git_dest` directory     |
|    `git_recursive`     | `false`  |    no    | bool |            Whether submodules should be cloned            |
| `git_track_submodules` | `false`  |    no    | bool |           Whether submodules should be tracked            |
|     `git_refspec`      |    ""    |    no    | str  |             Additional refspec to be fetched              |
|      `git_remote`      | `origin` |    no    | str  |                    Name of the remote                     |

## Dependencies

None.

## Example Playbook

```yaml
---
- name: Ensure git is installed and clone a repo
  hosts: all

  roles:
    - role: pumphouse_p.cicd.git
      vars:
        git_src: "https://github.com/pumphouse-p/peek-go.git"
        git_dest: "{{ ansible_env.HOME }}"
        version: "master"
```

## License

GPL

## Author Information

Devin Parrish ([GitHub](https://github.com/pumphouse-p))