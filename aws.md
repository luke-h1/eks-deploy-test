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
12. copy repo URI
13. go to ECS
14. go to clusters
15. create cluster > pick AWS fargate networking only > create new VPC > leave as default 
16. click view cluster
17. at this stage we need a task definition so go to task defs > create new task def > pick fargrate > name app > task role = none > leave default network mode > give task size defs > add container > paste image URI > add ports you've exposed in the docker image > leave everything as default > click create
18. go to cluster
19. create new service > click fargate > service name=app > number of tasks=1 > leave everything else as default > go to next step > select first subnet > leave everything else as default > do not autoscale > review & create service > go to view service > wait until service has finished provisioning 
20. once you have a public IP address you can assign that to DNS and you app is ready