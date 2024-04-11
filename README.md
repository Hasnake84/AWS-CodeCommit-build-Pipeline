# DevSecOps-Automation Project
This project implements a DevSecOps pipeline for integrating security scanning throughout the application development lifecycle within the AWS environment. The pipeline leverages various tools to identify and address security vulnerabilities early, ensuring a more secure and robust application.
# Objectives
# Code Repository (AWS CodeCommit) 
This serves as the central repository where developers store their application code.
# SonarCloud (SAST)
Performs Static Application Security Testing (SAST) by analyzing the application code directly in CodeCommit for vulnerabilities like SQL injection, insecure coding practices, and potential code smells.
# Snyk (SCA)
Conducts Software Composition Analysis (SCA) by scanning dependencies within the code for known vulnerabilities. This identifies potential risks introduced by third-party libraries used in the application.
# TruffleHog
Scans code for secrets like passwords, API keys, and other sensitive information that might be accidentally committed to the repository.
# Build and Test (AWS CodeBuild)
This service builds the application and executes the security scans mentioned above.
# Deployment Pipeline (AWS CodePipeline)
Orchestrates the entire development and security testing process.
# Upon a code commit in CodeCommit
- CodePipeline triggers a build in CodeBuild.
- CodeBuild retrieves the code, runs SonarCloud SAST, Snyk SCA, and TruffleHog scans, and integrates the results into the pipeline.
- CodePipeline evaluates the scan results. If vulnerabilities are detected, it can notify developers or prevent deployment until the issues are addressed.
# Dynamic Analysis (Zap Proxy) 
Zap Proxy is used as a Dynamic Application Security Testing (DAST) tool. DAST involves running the application to and analyze its behavior for vulnerabilities. This can be a valuable addition for a comprehensive security assessment.
Benefits:

- Create a repository on AWS CodeCommit
- IAM > Users > Select user > Security credentials > HTTPS Git credentials for AWS CodeCommit > Generate credentials > Save credential
- Clone repository Copy URL > Git > git clone https://git-codecommit_us-east-1..........
- Add code to the folder > Git > git add * > git commit -m "Added files" > Git push
- Create a buildspec.yml file
- Create organization project on SonalCloud for Static Application Security Testing (SAST)
- Update the buildspec.yml file with the SonalCloud project key, organization and token
- Using Git update buildspec.yml file with, git add * > git commit -m "buildspec file updated" > git push
- Create a CodeBuild Project instance on AWS > Start build
- Observe the build scan result on SonarCloud
- Add java files for unit test and better scan coverage
- Install TruffleHog and run a scan for leaked credential
- Config secret key in AWS secret manager > Store a new secret > Select other type of secret (API token) > Add the Key-name / Value-token
- Update buildspec.yml file as follows
    env:
    secrets-manager:
      TOKEN: sonarcloud1:tokenForSonar
      Dsonar.login=$TOKEN
 - Create a CI/CD Pipeline on AWS
 - Add a stage between Source and Build stage
 
