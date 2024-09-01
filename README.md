# Setting Up GitHub Actions to Deploy a Static Web Page to an S3 Bucket

  ![Output](https://github.com/Naimat250/CICD-Github-Actions/blob/6d7e4a9f00786828b8f5316ede31d1e8b9fd1466/images/output.PNG)
## Introduction:
  This project demonstrates a simple, yet powerful Continuous Integration/Continuous Deployment (CI/CD) pipeline for a static website using GitHub Actions and AWS S3. The aim of this 
  project is to automate the deployment process of a static website hosted on AWS S3 whenever code is pushed to the main branch of a GitHub repository.

 By leveraging the native integration of GitHub Actions with AWS, this setup streamlines the deployment process, ensuring that the latest version of the website is always up-to-date and 
 accessible via the internet. It is designed to be lightweight, cost-effective, and scalable, utilizing S3's static website hosting capabilities.

## Project Workflow:
### 1: Create a GitHub Repository:
- Initialize a new GitHub repository for managing the project’s code and configuration.

## 2: Create IAM User with S3 Access 
- Log in to the AWS Management Console.
- Create a new IAM user with programmatic access.
- Attach a policy granting the IAM user permission to manage and upload files to S3.
- Generate the Access Key ID and Secret Access Key.
- Store the credentials securely in GitHub Secrets (AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY).

## 3: Configure an S3 Bucket
- Create a new S3 bucket in AWS
- Enable static website hosting for the S3 bucket.
- Make the bucket public to allow access to website files.
- Apply a bucket policy to allow public read access to the hosted website content.
## 4: Create the GitHub Actions Workflow (main.yml)
- Add a .github/workflows/main.yml file to your repository.
- Configure the workflow to trigger on code pushes to the main branch.
## 4: Configure GitHub Actions Workflow Steps
- ## Checkout Code:
  - Use the actions/checkout@v1 action to pull the latest code from the repository.
- ## Configure AWS Credentials:
  - Use the aws-actions/configure-aws-credentials@v4 action to configure the AWS CLI with the credentials stored in GitHub Secrets.
- ## Deploy to S3:
  - Use the AWS CLI to sync the repository files to the S3 bucket using aws s3 sync . s3://<your-bucket-name> --delete.
## 5: Push Changes to GitHub
- When a change is made to the code, commit and push the changes to the main branch.
- GitHub Actions will automatically trigger and deploy the updated code to the S3 bucket.
## 6:Deployment Completion
- The static website will be updated automatically in the S3 bucket.
- Any outdated files in the bucket will be removed to ensure only the latest version of the site is hosted.

## 7: Accessing the Website through S3 URL
Once the deployment is completed and the website files have been successfully synced to the S3 bucket, you can access the static website using the S3 bucket's URL.
## http://naimatcicd.s3-website-us-east-1.amazonaws.com




