# kube-news

## 💡 Idea
In this small lab, I decided to build a portal for creating annotation in a small project based on node and running in a Docker and in the cluster in Kubernetes. To create the automation of the infrastructure I used the Terraform and after the automation of the creation of the replicas I used GitHub Action, and the cluster is running in the Digital Ocean provider.

---

### 🛠️ Build with
* Terraform
* Docker
* Docker Hub
* Kubernetes
* Digital Ocean
* GitHub Actions (CI/CD)

---

### 🧾 Prerequisites

- Terraform CLI;
- Kube;
- Key (API) for access the Digital Ocean;

---

### ✈️ Process

1. After the configuration of the tools, run the command ```terraform apply``` in the directory 'terraform' of the project. It's necessary to say "Yes" to accept the changes in the provider. When the finish the provision of the infrastructure, the code will create the file ``kube_config.yaml``, and this file will be used in the GitHub Actions (CI/CD) in the future to accept the connection in the Digital Ocean.

2. After the terraform creates the infrastructure, it's necessary to create the cluster using Kubernetes, when this cluster will create the node using Postgres for the database, and the node.js for the web server;

3. Run the deployment of the Kubernetes with the command ```kubectl apply -f deployment.yaml``` in the directory 'k8s' of the project.

4. Now the Kubernetes and cluster are done, it's possible to connect to the application and see the IP for LoadBalancer using the command ```kubectl get service```

5. Using the GitHub Actions to create the pipeline of CI/CD, where:
    - CI: Connect in the DockerHub for the build of the image node of the container and versioning of the image;
    - CD: Connect in the Kubernetes running in the DigitalOcean, apply the last version of the image in the node and apply for the numbers of the replicas.


### 🤔 Some lab considerations
My main goal with this project/lab was to start from scratch with these tools and start using Docker / Kubernetes / Terraform / GitHub Actions (CI/CD). I'm starting my studies to work as a DevOps, I believe there are more efficient and safer ways to do this process, but keep in mind that it was done by a student with a lot of desire to learn and do 😜

---