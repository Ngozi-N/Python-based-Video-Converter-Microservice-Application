<h2>Deploying a Python Microservices App on AWS with EKS, Docker, Helm, and RabbitMQ</h2><br>
<b>1. Setting up the Prerequisites</b><br>
Before getting started, I ensured that the following were installed and configured on my local environment:<br><br>

AWS CLI & IAM credentials<br>
kubectl<br>
Python<br>
Docker<br>
Helm<br><br>


<b>2. Creating the Kubernetes Cluster (EKS)</b><br>

I created an EKS cluster and node group. Once active, I confirmed the nodes (EC2 instances) were up and running.<br><br>


<b>3. Connecting EKS Cluster to CLI</b><br>

The cluster was then connected to the CLI using aws eks update-kubeconfig, allowing further operations using kubectl.<br><br>

<b>4. Deploying Databases and Message Queue</b><br>

The project uses the following backend services:<br>

MongoDB for the auth service<br>
PostgreSQL for token storage<br>
RabbitMQ for messaging between services<br>
All were deployed using Helm charts.<br><br>


<b>5. Building and Pushing Microservice Images</b><br>

Each service — auth, converter, gateway, and notification—was containerized using Docker. Images were pushed to Docker Hub.<br>

docker build -t your-image-name .<br>
docker push your-image-name<br><br>


<b>6. Deploying Microservices with Helm</b><br>

After building the images, I created Helm charts for each microservice and deployed them to the EKS cluster.<br><br>


<b>7. Verifying Functionality</b><br>

Received a token from PostgreSQL<br>
Accessed the email notification<br>
Successfully downloaded and played the converted MP3 file<br>
