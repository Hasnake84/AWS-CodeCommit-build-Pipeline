# DevSecOps-Automation Project

# AWS Code Commit-Build-Deploy-Pipeline

# Objectives
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
 
