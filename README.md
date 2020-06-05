# Serverless Seismic Processing using Lambda Functions on AWS

Example of using AWS for serverless on-demand seismic processing/calculations.  Being able to run Lambda functions in parallel without having to provision and compute resources (e.g. EC2 instances, clusters, file systems) greatly reduces the complexity of application being developed.  

We compare the performance and cost between doing the processing in a notebook/EC2 instance and use Lambda.

In this demo, we use Python (in SageMaker Notebooks) to do the following:
1. Read in the header information from a SEGY file
2. Calculate the trace mean amplitude for each trace
3. Provision up to 1000 Lambda functions to do the calculation instead
4. Store the resutls in S3
5. Display the results in the notebook

