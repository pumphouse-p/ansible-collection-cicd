# README for `cicd.go`

## Description

Installs the Go SDK, builds, and tests a Go application.

## Requirements

- `ansible.builtin`

## Variables

### Collection Scoped Configuration

|    Variable Name     | Default | Required | Type |                               Description                               |
|:--------------------:|:-------:|:--------:|:----:|:-----------------------------------------------------------------------:|
| `cicd_workspace_dir` |   ""    |   yes    | str  |                 Base directory where build files exist                  |
|  `cicd_output_file`  |   ""    |   yes    | str  | Filename relative to `cicd_workspace_dir` that contains compiled output |
|    `cicd_src_dir`    |   ""    |   yes    | str  |              Base directory containing `.go` source files               |

### Role Variables

|      Variable Name      |                 Default                 | Required | Type |                Description                |
|:-----------------------:|:---------------------------------------:|:--------:|:----:|:-----------------------------------------:|
|      `go_version`       |                `1.19.1`                 |    no    | str  |     Version of the Go SDK to install      |
|    `go_architecture`    |                 `amd64`                 |    no    | str  | CPU architecture of the Go SDK to install |
|      `go_sdk_url`       | `https://storage.googleapis.com/golang` |    no    | str  |       Base URL to download SDK from       |
|    `go_install_dir`     |        `/opt/go/{{ go_version}}`        |    no    | str  |          Local installation path          |
|    `go_download_dir`    | `{{ ansible_env.HOME }}/.downloads/go`  |    no    | str  |            Local download path            |
| `go_download_use_proxy` |                 `false`                 |    no    | bool |         Download through a proxy          |

## Dependencies

None.

## Example Playbook

```yaml
---
- name: Ensure go SDK is installed and build app
  hosts: all
  vars:
    cicd_workspace_dir: "{{ ansible_env.HOME }}/peek-go"
    cicd_src_dir: "./cmd/peek-go"
    cicd_output_file: "peek-go"

  roles:
    - role: pumphouse_p.cicd.go
      vars:
        go_version: "1.16.14"        
```

## License

GPL

## Author Information

Devin Parrish ([GitHub](https://github.com/pumphouse-p))