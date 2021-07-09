# End2end ML blueprint

This template is a potential starting point for all ML related projects. It gives a structure, integrates engineering best practices allowing data scientists to focus on experimenting while they leverage automated developer tools. They can turn their experiments into Kubeflow pipelines as well.


## Features

- reusable template built with cookie-cutter
- integrates experiment management with MLFlow with Kubeflow pipelines
- precommit hooks for code testing, linting, formatting, type checking
- CI/CD pipelines to test code, build artifacts, deploy pipelines
- terraform config to manage infrastructure components

## How to use

1. Deploy the blueprint from the AIP platform or directly with cookie-cutter

```shell
pip install cookiecutter
cookiecutter gh:aliz-ai/ml-end2end-blueprint
```
2. Add your own code to the template, customize where necessary.

## Project Structure

```
├── base_image                          <- A common container image that is used across all components in the pipeline.
├── ml_project                          <- Experiment definitons and entrypoints.
├── pipelines
│   └── components                      <- Python and other Kubeflow pipelines components.
├── project_common_code                 <- Packaged source code for the project
├── terraform                           <- Infrastructure component definition.
├── cloudbuild.yaml                     <- CI/CD steps definition.
└── setup_local_env.sh                  <- Handy script to set up local development environment.
```

## Repository URL

[https://github.com/aliz-ai/ml-end2end-blueprint](https://github.com/aliz-ai/ml-end2end-blueprint/)