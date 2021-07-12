# Manufacturing Optimization

Manufacturing Optimization is a service provided by Aliz Intelligence Platform. It can be used in optimization tasks, 
where setting values needs to be optimized to improve business KPI values depending on former setting values and 
external factors. This kind of problem setting usually appears in manufacturing industry where sensors provide 
mesaurements of external factors and business critical KPI values. 

## Features

- Automatic data cleaning based on ML best practices
- Scheduled retraining pipeline built with Kubeflow
- Simulation engine to assess optimization perfomrmance
- Multi-objective optimization with state-of-the art genetic agorithm
- Serving API endpoint with kubeflow serving


## How to use

The initial setup is performed by Aliz Data Scientists using first batch of historical data. 

1. Upload additional historical data. 
2. Wait for the retraining pipeline to finish.
3. Call API endpoint.

**Optimization endpoint input:**

- Current KPI values
- Current external data snesor values
- Current settings values

**Optimization endpoint response:**

- Optimized setting values
- Predicted optimized KPI values

## Project Structure

```
├── kubeflow                            <- Kubeflow specific implementation code
├── optimization                        <- Main code library, including optimization simulation engine.
└── terraform                           <- Infrastructure component definition.
```
