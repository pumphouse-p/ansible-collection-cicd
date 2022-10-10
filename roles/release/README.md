# README for `cicd.release`

## Description

Publishes a software release to a specified location.

## Requirements

- `amazon.aws`

## Role Variables

### Collection Scoped Configuration

|    Variable Name     | Default | Required | Type |                           Description                           |
|:--------------------:|:-------:|:--------:|:----:|:---------------------------------------------------------------:|
| `cicd_workspace_dir` |   ""    |   yes    | str  |             Base directory where build files exist              |
|  `cicd_output_file`  |   ""    |   yes    | str  | Filename relative to `cicd_workspace_dir` that contains release |

### General Configuration

|  Variable Name   | Default | Required | Type |                   Description                   |
|:----------------:|:-------:|:--------:|:----:|:-----------------------------------------------:|
| `release_target` |   ""    |   yes    | str  | Target system where release should be published |

### Release Target Configuration (`s3`)

The following variables are supported when publishing a release to Amazon S3.

|         Variable Name          | Default | Required |     Type      |                          Description                          |
|:------------------------------:|:-------:|:--------:|:-------------:|:-------------------------------------------------------------:|
|      `release_s3_bucket`       |   ""    |   yes    |      str      |       The name of the bucket to publish the release to        |
|    `release_s3_object_name`    |   ""    |   yes    |      str      |                    The name of the object                     |
|       `release_s3_tags`        |   ""    |    no    | dict(str:str) |                   Tags to assign to object                    |
| `release_s3_bucket_versioning` | `true`  |    no    |     bool      |       Whether bucket versioning is enabled or disabled        |
|   `release_s3_bucket_create`   | `true`  |    no    |     bool      | Whether bucket should be created if it does not already exist |


## Dependencies

None.

## Example Playbook

```yaml
---
- name: Playbook to manage records in Cloudflare
  hosts: localhost
  gather_facts: false
  become: false

  roles:
    - role: pumphouse_p.cicd.release
      vars:
        release_target: "s3"
        release_s3_bucket: "mybucket"
        release_s3_object_name: "myrelease"
        release_s3_tags:
          version: "1.0"
```

## License

GPL

## Author Information

Devin Parrish ([GitHub](https://github.com/pumphouse-p))