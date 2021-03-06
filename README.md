# Performing Calculations on Seismic Data using AWS Lambda

This is an example of using AWS services for serverless on-demand seismic calculations.  The ability to run Lambda functions in parallel without having to provision any compute resources (e.g. EC2 instances, clusters, file systems) greatly reduces the complexity of the workflow and underlying code.  

When you do processing in a SageMaker Notebook, you are limited to the power of the EC2 computer instance underlying it and the network bandlimits.

![title](images/Page-1.png)

However, you can refactor your code into a Lambda function and process the seismic data in many smaller pieces, with each Lambda having it's own vCPU and network bandwidth.  This can cut the overall time to process the data dramatically with very minimal coding.

![title](images/Page-2.png)

Once you have completed you testing in a SageMaker Notebook, you can make the code automated by integrating it with Step Functions to orchestrate the processing steps and EventBridge to trigger the workflow.  Other services can trigger the workflow.  An example is S3 can trigger the workflow once a new seismic file is uploaded into a particular bucket and pass the needed information to the Step Functions.

![title](images/Page-3.png)

In the provided Jupyter notebooks that can be used with Amazon SageMaker, we will compare the performance between doing the processing on an EC2 instance versus using on-demand Lambda with 3 different seismic files.  The provided CloudFormation template will spin up the required AWS services and permissions to run this workshop.  Once completed, simply remove the stack from your account.

## Installation
1. Create an AWS account.
2. Download the CloudFormation template **Seismic_Calculations_CloudFormation_Template_????.yaml** this is appropriate for the AWS region you will be working in.
3. From the AWS console, navigate to **CloudFormation**.
4. Click on **Create Stack**.
5. Keep **Template is Ready** selected above, then select **Upload a template file** below.
6. Upload the **Seismic_Calculations_CloudFormation_Template_????.yaml** file and click **Next**.
7. On the next page, give the stack a descriptive name, such as **Seismic-Lambda-Calculations**.
8. Define an S3 bucket name to be created (it has to be a unique name globally, so using your name works well).
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
4. Store the results in S3.
5. Display the results in the notebook.

## Uninstall
1. From the AWS console, navigate to **CloudFormation**.
2. Select the stack you created then click the **Delete** button above.

### Note
The notebooks no.1 and no.2 use the seismic volumes publically available from the Equinor Volve Data Village dataset and are designed to be run back to back.  The no.3 notebook uses the Australian Government Poseidon dataset and is designed to be run by itself.  Check the license agreement of the data before usage.  Anyone who wants to follow the workshop and not use their own SEGY files should download the required files independently and upload them to an AWS S3 bucket.  Alternatively, you can provide your own SEGY files, though due to variations in SEGY revisions and data types, the provided Python code might not decode them correctly and might need to be adjusted.

### Author
Constantine Vavourakis (AWS, Sr. Solutions Architect)
