# tekton-build-task
Tekton for building and pushing docker image with Kaniko

## Pre-requisites
1. Create docker registry K8s secrets, replace **DOCKERHUB_USERNAME**, **DOCKERHUB_PASSWORD**, **DOCKERHUB_EMAIL** by appropriate ones
```console
kubectl create secret docker-registry dockercredential --docker-server=https://index.docker.io/v1/ --docker-username=<DOCKERHUB_USERNAME> --docker-password=<DOCKERHUB_PASSWORD> --docker-email <DOCKERHUB_EMAIL>
```
2. Deploy Tekton on the cluster
```console
kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
```
3. Install Tekton Cli

## Deploy Tekton build task
```console
kubectl apply -f tekton-build-task.yaml
```
## Follow Logs for Tekton build task run with Tekton cli
```console
tkn taskrun logs build-docker-image-from-source-task-run -f
```
