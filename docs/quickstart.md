## Installation instructions 
Version 9.15

Created on 15-Nov-2020.
 
### Quick Start:
#### Control-M Integration to AWS Glue jobs.

This plugin is based on the AWS recommended sdk integration with AWS Glue.

https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-python-calling.html
 
### Installation Details
Prerequisites and installation notes:

    1.) Control-M Agent V9.0.20x or higher on a supported Linux or Windows environment with the Application Integrator CM V9.0.20x or higher
    2.) AWS access keys for programmatic access
   
#### Authentication:
This plugin uses the AWS recommended access key ID and secret access key for programmatic access.

No username and passwords are used.
For details regarding AWS access key authorization, please visit the AWS authentication page by using the link below

https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html
   
#### 1. Download the AWS Glue job 
http://github.com/awsglueaijob.

##### Watch an introduction video on Application Integrator
[AppIntVideo](https://youtu.be/7CshwZYMPWw)

#### 2. Deploy the plugin.
        a. Using the Application Integrator UI
        b. Using the Control-M Automation API  
    
         
![aideploy](./images/gluedeployscrn.png)
        
           
#### 3. Define a connection profile

##### Connection Profile: Used for authenticating with AWS
    Add a new connection profile from the Configuration Manager.

![configmanager](./images/gluconnprofstart.png)

    Input the required fields
    Note: The AWS secret key will be encrypted at entry.

![connectionprofile](./images/gluconnprofdetails.png)

#### 4. Define an AWS Glue trigger job in Control-M

##### Job palette - Drag and drop your jobtype into a folder

![palette](./images/glupalette.png)

##### Job Definition panel
 See the Job Parameter table below for details
 
![jobfields](./images/glujobdetails.png)
    
    ===== Glue Trigger Job Parameters Description =====

| Field | Value |
| --- | --- |
| Connection Profile | The name of the predefined connection profile containing aws keys defined in the connection profile step 3 above
| Glue Job Name | The name of the Glue Job in AWS Glue that you wish to run. |
| Glue Job Arguments | Optional glue job arguments supplied in the below format |
| Arguments format | {'--Key1': 'value', '--Key2': 'value'} |
| |If there are no Job Arguments then leave the text field empty|
| Job Monitor Interval | The polling time in seconds that your job status should be verified

 


#### 5. You can also choose to build your Glue trigger job in Control-M Automation API using jobs-as-code

Control-M automation api allows for the creation of jobs in a JSON format.
Once you have deployed the AWS Glue plugin you have immediate support for the creation of AWS Glue jobs
in JSON format.

Sample JSON

```
{
  "glue_args": {
    "Type": "SimpleFolder",
    "ControlmServer": "production",
    "OrderMethod": "Manual",
    "AI AWS Glue Offic_Job_2": {
      "Type": "Job:ApplicationIntegrator:AI AWS Glue Offic",
      "ConnectionProfile": "NCUPRO",
      "AI-Glue Job Name": "ncu-hashtbl-etl",
      "AI-Glue Job Arguments": "{'--source': 'ncu-writefolder', '--destination': 's3://ncu-datapipe/write/'}",
      "SubApplication": "Glue",
      "Host": "appintagent",
      "CreatedBy": "emuser",
      "RunAs": "NCUPRO",
      "Application": "AWS"
    }
  }
}
``` 
    
#### 6. Run your first AWS Glue job from Control-M


#### 7. The Troubleshooting guide can be found at the following link
https://pmbmc.github.io/ifdocs/#/glue_troubleshooting

##### Performance:
Performance is dependant on your connectivity to AWS. Control-M jobs do not affect the performance of the AWS jobs
themselves. Control-M performs the triggering, monitoring and supplied completion status and information of the jobs.

Note:
    The current job type has been tested on Linux
 
 #### Return to AWS Glue plugin Introduction

https://pmbmc.github.io/awsgluedocs/

