# Forecasting blueprint

The aim of this project is to create a product- and industry-agnostic forecasting engine. The engine is powered by both statistical forecasting methodologies with state-of-the-art technologies. With this engine, Clients can conveniently train, interpret and serve forecasting models at scale.

## Features

- runs model training and serving on Kubeflow
- leverages proven technology stack and cloud infrastucture from GCP 
- serves, at a predefined frequency (daily, weekly, monthly), future values of a KPI
- combines SARIMAX, TFT and Prophet as well as ensemble of these three models to create forecasts
- provides actionable insights on the provided time series data as well as the resulting forecasting models

## How to use

There are two main parts in the code now: the Kubeflow Pipeline implemented in a Python file and a Python library packaged as base image for the pipeline components.

To use this code you need to:

- Upload time series datasets as csv files on Google Cloud Storage
- Modify the provided .yaml file 
- Build the base Docker image
- Push the Docker image to repository
- Compile Kubeflow Pipeline
- Upload the Pipeline on Kubeflow UI
- Create a Pipeline Run on Kubeflow UI
- Later steps 5. to 7. can be automatized with a Python script.

### Prerequisites
Set GCP project and export it as a shell variable.
```
gcloud config set project forecast-product-proto-sandbox
export PROJECT=$(gcloud config list project --format "value(core.project)")
```
### Build Docker container via CloudBuild
You have the option to build and push the container in one step via CloudBuild by executing the following command, from project root directory:
```
gcloud builds submit --config kubeflow/pipelines/base/cloudbuild.yaml
```
### Compile Kubeflow pipeline
The Kubeflow Pipeline is defined in kubeflow/pipelines/pipelines directory.

To use the pipeline you have to compile it with the `dsl-compile `command.

The command is part of the Kubeflow Pipelines SDK. To have access to this command the SDK have to be installed:
```
pip3 install kfp --upgrade
```
After the dsl-compile command is available we can compile the pipeline:
```
dsl-compile --py "./kubeflow/pipelines/pipelines/Forecast training pipeline.py" --output Forecast_training_pipeline.yaml
dsl-compile --py "./kubeflow/pipelines/pipelines/Forecast serving pipeline.py" --output Forecast_serving_pipeline.yaml
```
### Using the Pipeline
Now that we have the pipeline compiled we can use it with the Kubeflow Central Dashboard by upload as a new Pipeline or by uploading as a new version of a Pipeline. After uploading it as brand new pipeline or a new version we can create a run and execute the pipeline.

## Project Structure

```
├── kubeflow                 
│   ├──  base                <- Packaged source code for the project
│   └──  pipelines           <- Kubeflow serving and training pipeline definitions and a project-specific yaml file to be adjusted
└── README.md                <- Detailed instructions to run the project
```

## Repository URL

[https://github.com/aliz-ai/forecast-product-proto](https://github.com/aliz-ai/forecast-product-proto)