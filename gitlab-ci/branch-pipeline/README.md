# GitLab CI branch pipeline template

This will enforce running of a pipeline for all commits on any branch.

## Usage

Add the following to a `.gitlab-ci.yml` file in the root of your GitLab repository:

    include: https://raw.githubusercontent.com/uktrade/webops-sre-tooling/main/gitlab-ci/branch-pipeline/gitlab-ci.yml
