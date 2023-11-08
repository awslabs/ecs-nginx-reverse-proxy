# NGINX Reverse Proxy on Amazon EC2 Container Service

__Note: There is an updated version of this reference available at: ["NGINX reverse proxy sidecar for a web container hosted with Amazon ECS and AWS Fargate"](https://containersonaws.com/pattern/nginx-reverse-proxy-sidecar-ecs-fargate-task)__

[NGINX](https://www.nginx.com/resources/wiki/) is a high performance HTTP server and reverse proxy which has achieved significant adoption because of its asynchronous event driven architecture which allows it to serve thousands of concurrent requests with very low memory footprint.

[Amazon EC2 Container Service](https://aws.amazon.com/ecs/) (ECS) is a highly scalable, high performance container management service that supports Docker containers and allows you to easily run applications on a managed cluster of Amazon EC2 instances.

This reference architecture shows how to run NGINX containers on a fleet of instances using ECS. You can [deploy Nginx as a basic static HTTP file server](/static-host). Or you can [deploy an Nginx reverse proxy container in front of an application container](/reverse-proxy).
