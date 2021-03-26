# Serverless seismic calculations using Lambda on AWS

This is an example of using AWS services for serverless on-demand seismic calculations.  The ability to run Lambda functions in parallel without having to provision and compute resources (e.g. EC2 instances, clusters, file systems) greatly reduces the complexity of the workflow.  Furthermore, using SageMaker notebooks and the provided code allows for easy ingestion of the data into different AWS services and Machine Learning technologies provided within SageMaker.  

In the provided notebooks, we will compare the performance and cost between doing the processing in a notebook instance versus using Lambda.  The provided CloudFormation template will spin up the required AWS services and permissions to run this workshop.  Once completed, simply remove the stack from your account.

Steps:
1. Read in the header information of a SEGY file
2. Calculate the trace mean amplitude for each trace in SageMaker as a benchmark
3. Provision up to 1000 Lambda functions to do the calculation in parallel
4. Store the resutls in S3
5. Display the results in the notebook

Note:
The workshop uses the seismic volumes publically available from the Equinor Volve Data Village dataset.  Anyone following the workshop should download the required files independently and host them on AWS S3.  Alternatively, you can provide your own SEGY files, though due to variations in SEGY revisions and data types, the provided Python code might not decode them correctly and will need to be adjusted.

Author:
Constantine Vavourakis (AWS, Solutions Architect)
