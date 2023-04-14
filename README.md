# WebOps SRE Tooling

A place for things we use to help us do our work, e.g. Docker images to perform tasks in pipelines.

## Development setup

    pip install -r requirements_dev.txt
    pre-commit install

## What's in here

* Gitlab CI
  * [GitLab CI branch pipeline template](./branch-pipeline/README.md)
  * [Terraform quality checks GitLab CI pipeline template](./terraform-quality-checks/README.md)
* [tfenv Docker image](./tfenv/README.md)
