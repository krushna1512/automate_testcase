---
name: Microservice-Setup-and-Deployment.
about: Step-by-step process of Microservices Setup and Deployment
title: Task-Microservice-Setup-and-Deployment
assignees: ['krushnasharma15']
---

## Process

**1. Github**
- [ ] Create a Repo (Use API Calls)
- [ ] Add permission to the particular team (API Call)

**2. Deployment Preparation (Requirement from Team)**
- [ ] Check.[aws/config.sh](http://aws/config.sh)  (if cron then add -cron in service name )(add cron parameter to build workflow file similar to yap-campaign repo )
- [ ] Create ECR (.aws/ecr-prepare.sh) (on two regions ) 
   (To run the above command you have use below commands )
        **aws configure get region
        export AWS_PROFILE=resortent-ap
        sh .[aws/ecr-prepare.sh](http://aws/ecr-prepare.sh)
        export AWS_PROFILE=resortent
        sh .[aws/ecr-prepare.sh](http://aws/ecr-prepare.sh)**

**Refer below steps to create AWS account profiles in your local system (Ignore if already done)**
- Go to home/.aws/credentials to add the credentials of your AWS account

[default]

aws_access_key_id = YOUR_DEFAULT_ACCESS_KEY_ID

aws_secret_access_key = YOUR_DEFAULT_SECRET_ACCESS_KEY

[us-east-1]

aws_access_key_id = YOUR_US_EAST_1_ACCESS_KEY_ID

aws_secret_access_key = YOUR_US_EAST_1_SECRET_ACCESS_KEY

- [ ] Run Lifecycle Policy ([.aws/ecr-lifecycle-policy.json)
- [ ] Check build.yaml and deploy,yaml make necessary changes if needed.
- [ ] Check CF template add necessary variables if required

**3. Deployment**
- [ ] Run build.yml from workflows (Add "cron: true" in the last line if you want to build it for cron)
- [ ] Run deploy.yaml

**4. Update AWS API gateway**
- [ ] Download the file to add the new path name and port number (API_Gateway > Stages > Export > OpenAPI3 > Export as OpenAPI 3 + API Gateway Extensions > JSON)
- [ ] Import API in API Gateway (Resources > Actions > Import API > (Paste the edited file here) > Select Import Modde "Overwrite" > Import)
- [ ] Deploy API (Actions > Deploy API)

**Note** (Use this file for new Port Number - https://docs.google.com/spreadsheets/d/1Aa1l_MzeOsrnb6FpBrkA9dX5fgXBhtUV34WACBLtI7g/edit#gid=0)
