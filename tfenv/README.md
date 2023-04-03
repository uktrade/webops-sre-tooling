# tfenv Docker image

For use in pipelines to simplify checking with multiple versions of Terraform. E.g. the currently used version of Terraform for a project and the latest release to get a headsup for anything that would need sorting before we can use it.

The latest version of the image is published as...

    gcr.io/sre-docker-registry/webops-sre-tooling/tfenv:latest

## Cloud Build configuration

Two Cloud Build configurations are provided here:
- `cloudbuild-work-in-progress.yaml` - for triggers on commits to any branch other than `main`. Builds an image for testing tagged with the commit SHA.
- `cloudbuild-main.yaml` - for triggers on merge to `main`. Builds an image tagged with the commit SHA and `latest`.
