# Serverless seismic calculations using Lambda on AWS

This is an example of using AWS for serverless on-demand seismic calculations.  The ability to run Lambda functions in parallel without having to provision and compute resources (e.g. EC2 instances, clusters, file systems) greatly reduces the complexity of the workflow.  

In the provided SageMaker notebooks, we will compare the performance and cost between doing the processing in a notebook instance versus using Lambda.

In this demo, we use Python (in SageMaker Notebooks) to do the following:
1. Read in the header information of a SEGY file
2. Calculate the trace mean amplitude for each trace in SageMaker as a benchmark
3. Provision up to 1000 Lambda functions to do the calculation in parallel
4. Store the resutls in S3
5. Display the results in the notebook

