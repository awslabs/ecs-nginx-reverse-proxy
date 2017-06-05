## NGINX Static Host Task Definition for ECS

1. Customize the content that you wish to serve, by changing files inside the `/srv` directory.
2. Build your NGINX container:
   ```
   $ docker build -t nginx_sample .
   ```
3. Create an EC2 Container Registry to push your NGINX container to:
   ```
   $ aws ecr create-repository --repository-name nginx
   ```
4. Authenticate with your new repository:
   ```
   $ `aws ecr get-login`
   ```
5. Tag your image and push your NGINX container to the repository. (You must put it your own repository URI from the `repositoryUri` value from step #3)
   ```
   $ docker tag nginx_sample <repo uri>:revision_1
   $ docker push <repo uri>:revision_1
   ```
6. Modify `task-definition.json` with the the image URL you just pushed to your ECR:
   ```
   {
     "containerDefinitions": [
       {
         "name": "nginx",
         "image": "<repo uri>:revision_1",
         "memory": "256",
         "essential": true,
         "portMappings": [
           {
             "containerPort": "8000",
             "protocol": "tcp"
           }
         ]
       }
     ],
     "volumes": [],
     "networkMode": "bridge",
     "placementConstraints": [],
     "family": "nginx"
   }
   ```
7. The above task definition will launch your NGINX container, with the container's port bound to a dynamically chosen port on one of your ECS hosts. To direct web traffic to that dynamic port you will want to [create an ALB and associate it with your ECS service](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-application-load-balancer.html).
