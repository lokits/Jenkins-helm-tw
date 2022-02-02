
### Implementation details:
Diagram:

<img width="200" alt="Screenshot 2022-02-02 at 11 53 48 AM" src="https://user-images.githubusercontent.com/90750786/152104489-db104160-deef-41c0-99a0-6c1047a20990.png">

### Services used:
##### GitHub
##### Jenkins
#### ArgoCD
#### Kubernetes
#### AWS (ECR,S3,EKS,EC2)
# CI/CD flow:
### CI Flow:
```
1. The developer will merge the code into the respective branch (e.g: tw-poc)
2. Webhook will trigger which is defined inside respective Github repository
3. Jenkins will start cloning the repo based on the script stages defined
4. The next stage would build the docker image by reading Dockerfile
5. Login into the Dockerhub repo and then it will push the image into DockerHub
6. At the end, it will update the image version in springboot helm chart repo inside values.yaml file
```
### CD Flow:
```
7. Whenever image version is updated ArgoCD will automatically take the version.
8. Then deployed the application into kubernetes at namespace level (thought-works)
9. Access the application with LB DNS Name
