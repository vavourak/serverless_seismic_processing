# Performing Calculations on Seismic Data using AWS Lambda

This is an example of using AWS services for serverless on-demand seismic calculations.  The ability to run Lambda functions in parallel without having to provision any compute resources (e.g. EC2 instances, clusters, file systems) greatly reduces the complexity of the workflow and underlying code.  

In the provided Jupyter notebooks that can be used with Amazon SageMaker, we will compare the performance between doing the processing on an EC2 instance versus using on-demand Lambda.  The provided CloudFormation template will spin up the required AWS services and permissions to run this workshop.  Once completed, simply remove the stack from your account.

## Installation
1. Download the CloudFormation template **Seismic_Processing_CF_Template.yaml**.
2. Create an AWS account.
3. From the AWS console, navigate to **CloudFormation**.
4. Click on **Create Stack**.
5. Keep **Template is Ready** selected above, then select **Upload a template file** below.
6. Upload the **Seismic_Processing_CF_Template.yaml** template you downloaded and click **Next**.
7. On the next page, give the stack a descriptive name, such as **Seismic-Calculations**.
8. Define an S3 bucket name to be created (it has to be a unique name globally, so using your name usually works).
9. Define a notebook name for SageMaker that is unique in your account.
10. Click **Next** to go to the **Configure stack options** page.  Click **Next** again.
11. On the **Review** page, scroll to the bottom and check the checkbox confirming that AWS resources will be created and click **Create Stack**.
12. After stack has been completed and resources created, navigate to **SageMaker**.
13. On the left sidebar, expand **Notebook** and select **Notebook Instances**.  Here you will see the Jupyter notebook instances in your account, including the one you just created.
14. Click the **Open Jupyter** next to the instance you created. It should have the two notebooks already uploaded.

## Calculation Steps
1. Read in the header information of a SEGY file.
2. Calculate the trace mean amplitude for each trace in SageMaker as a benchmark.
3. Provision up to 1000 Lambda functions to do the calculation in parallel.
4. Store the resutls in S3.
5. Display the results in the notebook.

## Uninstall
1. From the AWS console, navigate to **CloudFormation**.
2. Select the stack you created then click the **Delete** button above.

### Note
The workshop uses the seismic volumes publically available from the Equinor Volve Data Village dataset, licensing permitting.  Anyone who wants to follow the workshop and not use their own SEGY files should download the required files independently and upload them to an AWS S3 bucket.  Alternatively, you can provide your own SEGY files, though due to variations in SEGY revisions and data types, the provided Python code might not decode them correctly and might need to be adjusted.

### Author
Constantine Vavourakis (AWS, Sr. Solutions Architect)
