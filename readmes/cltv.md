# Customer Lifetime Value 

Predicting customer lifetime value is a way of identifying those customers who potentially generate the majority of your sales revenue. With this model, you can tailor advertisements to individuals or groups of similar users and target your most valuable customer segments.


## Features

- ingest customer transaction history from BigQuery
- automatic feature generation with BigQuery
- model building with BigQueryML
- scheduled training and prediction pipelines built with Kubeflow
- exploratory notebook to observe model details

## How to use

1. In order to use the blueprint you must customize the configuration file within the pipelines folder for your dataset.
2. Then deploy the necessary infrastructure components with terraform.
3. Commit the changes back to the repository and let the CI/CD pipeline deploy and run the pipelines.

## Project Structure

```
├── base_image                          <- A common container image that is used across all components in the pipeline.
├── notebooks                           <- Notebooks to develop and test the pipeline components locally.
├── pipelines
│   └── components                      <- Python and other Kubeflow pipelines components.
├── terraform                           <- Infrastructure component definition.
└── cloudbuild.yaml                     <- CI/CD steps definition.
```

## Repository URL

[https://github.com/aliz-ai/cltv_blueprint/](https://github.com/aliz-ai/cltv_blueprint/)