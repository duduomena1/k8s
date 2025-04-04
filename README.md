# Kubernetes Study Repository

This repository contains various Kubernetes configurations and examples to help understand and practice Kubernetes concepts.

## Files and Descriptions

### `lb-service.yml`
This file defines a Pod and a LoadBalancer Service for a web application.

- **Pod**:
    - Name: `frontend-srv`
    - Container: `apache-pod` using the `httpd` image, exposing port 80.
- **Service**:
    - Name: `front-srv-lb`
    - Type: `LoadBalancer`
    - Selector: `type: web-app`
    - Ports:
        - Port: 80
        - TargetPort: 80
        - NodePort: 30008

### `livenessprob.yml`
This file defines a Pod with a liveness probe to check the health of the container.

- **Pod**:
    - Name: `liveness-pod`
    - Container: `livess-test` using the `busybox` image.
    - Liveness Probe:
        - Command: `cat /tmp/healthy`
        - Initial Delay: 5 seconds
        - Period: 5 seconds
        - Failure Threshold: 3

### `resources-pod.yml`
This file defines a Pod with resource requests and limits for its containers.

- **Pod**:
    - Name: `resources-pod`
    - Containers:
        - `apache-cont` using the `httpd` image
            - Requests: 500m CPU, 128Mi memory
            - Limits: 1000m CPU, 256Mi memory
        - `redis-cont` using the `redis` image
            - Requests: 400m CPU, 64Mi memory
            - Limits: 500m CPU, 128Mi memory

## Usage

To apply these configurations, use the following `kubectl` commands:

```sh
kubectl apply -f lb-service.yml
kubectl apply -f livenessprob.yml
kubectl apply -f resources-pod.yml
```

## Learning Objectives

- Understand how to define and use Pods in Kubernetes.
- Learn how to configure Services, including LoadBalancer types.
- Implement liveness probes to monitor container health.
- Set resource requests and limits for containers to manage resource allocation.

## Prerequisites

- Kubernetes cluster
- `kubectl` command-line tool

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.