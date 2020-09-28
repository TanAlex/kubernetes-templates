# Overview
| File | Purpose | 
| ---      |  ------  |
| deployment.yml | Deploys the NGINX pods to handle incoming requests |
|load-balancer.yml |Launches the AWS LoadBalancer that forwards all requests to the NGINX deployment |
|namespace.yml | Creates the namespace to logically separate the resource deployment |
|nginx-config.yml | Configures the NGINX deployment<br> https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/configmap/ |
| role.yml   | Grants the deployment access to perform necessary operations  | 