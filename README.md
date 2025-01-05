# Provision Cloud Infrastructure
Use Terraform to create the Kubernetes cluster.

Navigate to the terraform/ directory:
cd terraform/
Initialize Terraform:
terraform init
Apply the Terraform configuration:
terraform apply
Export the kubeconfig file to interact with your Kubernetes cluster:
export KUBECONFIG=<path_to_generated_kubeconfig>

# Build and Push Docker Image
Navigate to the web-app/ directory:
cd web-app/
Build the Docker image:
docker build -t your-docker-repo/web-app:latest .
Push the Docker image to your container registry:
docker push your-docker-repo/web-app:latest

# Deploy Kubernetes Resources
Navigate to the k8s/ directory:
cd ../k8s/
Apply the Kubernetes manifests:
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

# Configure Monitoring
Create a namespace for monitoring:
kubectl create namespace monitoring
Deploy Prometheus:
kubectl apply -f prometheus/prometheus-config.yaml
kubectl apply -f prometheus/prometheus-deployment.yaml

# Access the Application
Retrieve the LoadBalancer IP of the web application:
kubectl get service web-app-service
Open the IP in your browser to view the static web application.

# Access Prometheus Monitoring
Retrieve the Prometheus service IP:
kubectl get service prometheus -n monitoring
Open the IP in your browser with port 9090 to access the Prometheus UI.
