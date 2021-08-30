# NGINX Reverse Proxy on Amazon EC2 Container Service

## Enian Notes:
Used in the ECS Instance described in Weaver repo under the task definition `nginx`.
Any changes to this need to be manually pushed to ECR.

```aidl
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 562715099132.dkr.ecr.eu-west-1.amazonaws.com

docker build -t kf-reverse-proxy-repo .

docker tag kf-reverse-proxy-repo:latest 562715099132.dkr.ecr.eu-west-1.amazonaws.com/kf-reverse-proxy-repo:latest

docker push 562715099132.dkr.ecr.eu-west-1.amazonaws.com/kf-reverse-proxy-repo:latest
```

----

[NGINX](https://www.nginx.com/resources/wiki/) is a high performance HTTP server and reverse proxy which has achieved significant adoption because of its asynchronous event driven architecture which allows it to serve thousands of concurrent requests with very low memory footprint.

[Amazon EC2 Container Service](https://aws.amazon.com/ecs/) (ECS) is a highly scalable, high performance container management service that supports Docker containers and allows you to easily run applications on a managed cluster of Amazon EC2 instances.

This reference architecture shows how to run NGINX containers on a fleet of instances using ECS. You can [deploy Nginx as a basic static HTTP file server](/static-host). Or you can [deploy an Nginx reverse proxy container in front of an application container](/reverse-proxy).
