# hackathon-2016-12

## Docker Notes

#### Reference Docs
* [Dockerizing a Node.js web app](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)

1. `scripts/buildit`: Builds the docker image
2. `docker images`: list images
3. `docker rmi <image id>`: remove image
4. `docker run -p 3030:3000 -d <image id>`: Run image mapping private port 3000 to public (external) port 3030
5. `docker ps -a`: show all running containers

## Google Cloud SDK Notes

#### Reference Docs
* [Google Cloud SDK Documentation](https://cloud.google.com/sdk/docs/)

1. ./google-cloud-sdk/bin/gcloud init

## Kubernetes Notes

####  Reference Docs
* [Pushing to Container Registry ](https://cloud.google.com/container-registry/docs/pushing)
* [Creating Single-Container Pods](http://kubernetes.io/docs/user-guide/pods/single-container/)

1. `scripts/pushit`: Tags and pushes the docker image to my docker registry in GC. If it hangs and can't ping the repo server then likely it's a proxy configuration issue with docker (on the Mac I had to set proxies using the Docker preferences).
2. To deploy, go to your [Kubernetes Console](https://console.cloud.google.com/kubernetes/list), click on Conainer Clusters, the click "Connect" for your cluster and follow the instructions to start a local admin dashboard for your cluster
3. Then you can go to [http://localhost:8001/ui](http://localhost:8001/ui)

    Click Pods then Create (in the upper right). To get your image URL you will need to go to the Container Engine Console click on the image in your Registry and click "Show pull command". It will look something like:  us.gcr.io/ecstatic-magpie-152317/server.js:v2. And don't forget to mark the service as external and map your incomming port (Port) to the port the container's port (Target Port)

    After provisioning click on Services and you should see an External endpoints
