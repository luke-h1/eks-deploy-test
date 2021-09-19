1. search ECR on AWS (container registery)
2. install AWS CLI 
3. create user and give them keys via aws-configure
4. get user id by going to my account account 
5. URL is <userID>.dkr.ecr.<region>.amazonaws.com
6. login to ecr by doing the following: 
aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin <userid>.dkr.ecr.eu-west-2.amazonaws.com
7. tag image: docker tag app <uid>.dkr.ecr.eu-west-2.amazonaws.com/<name of app>
8. push image: ocker push <uid>.dkr.ecr.eu-west-2.amazonaws.com/<name of app> 
9. at this point you will get the following error: name unknown: The repository with name 'app' does not exist in the registry with id '<user_id>'
10. create the app. go to ecr > create repo > private repo > leave default > create
11. repush the image