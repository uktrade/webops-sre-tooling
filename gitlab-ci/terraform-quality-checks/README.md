# Terraform quality checks GitLab CI pipeline template

This runs some basic checks on Terraform files in a GitLab CI pipeline.

It will expect the following environment folder structure for your Terraform:

    .
    └── env
        └── dev
        └── prod

## Usage

Add the following to a `.gitlab-ci.yml` file in the root of your GitLab repository:

    include: https://raw.githubusercontent.com/uktrade/webops-sre-tooling/main/gitlab-ci/terraform-quality-checks/gitlab-ci.yml

If your repository does not have `env/dev` OR `env/prod`, you can set these variables to false:

    variables:
      HAS_DEV_TERRAFORM: 'false'
      HAS_PROD_TERRAFORM: 'true'
