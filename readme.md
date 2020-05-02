# Docker hub image - abhinabsarkar/abs-aspnetapp:v1
A sample docker app built on Alpine linux 3.1 version using C# dotnet core version 3.1. The sample application returns the details of the server on which it runs, including the host name & ip address.

The docker image can be downloaded from docker hub by running the below command 
```bash
docker pull abhinabsarkar/abs-aspnetapp:v1.
```
Size of the docker image is 110 MB.

### To build the image, run docker build from the root directory of the application
```bash
# Build the abs image
docker build -t abs-aspnetapp:v1 .
# Run the docker container locally
# The release version runs the container at port 80 although the app is running at port 5000
docker run --name abs-aspnetapp-container -d -p 8002:80 abs-aspnetapp:v1
# Check the status of the container
docker ps -a | findstr abs-aspnetapp-container
# Test the app
curl http://localhost:8002
# log into the running container 
docker exec -it abs-aspnetapp-container /bin/bash
docker exec -it abs-aspnetapp-container <command>
# Remove the container
docker rm abs-aspnetapp-container -f
# Remove the image
docker rmi abs-aspnetapp:v1
# Push the image to docker hub
docker login
# Tag the local image & map it to the docker repo
docker tag local-image:tagname new-repo:tagname
# eg: docker tag abs-aspnetapp:v1 abhinabsarkar/abs-aspnetapp:v1
# push the tagged image to the docker hub
docker push new-repo:tagname
# eg: docker push abhinabsarkar/abs-aspnetapp:v1
```