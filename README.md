📊 Employee Task Management System

## Overview
The Employee Task Management System is a robust web application developed using Python and Django, designed to streamline employee task management. It enables efficient task assignment, tracking, and provides analytical insights through an interactive dashboard using Matplotlib. Anaconda is recommended for an isolated and secure development environment.

## ✨ Key Features
- **🐂 Task Management**: Assign, track, and update employee tasks with ease.
- **🔒 User Authentication**: Secure login and role-based access control for employees and administrators.
- **📊 Analytical Dashboard**: Gain insights into task completion and performance metrics with Matplotlib.
- **📁 Reporting**: Generate detailed reports on employee efficiency and task progress.
- **🛠️ Admin Interface**: Manage users, tasks, and system settings through Django Admin.



## 🚀 Installation Guide
### **1️⃣ Clone the Repository**
```sh
git clone https://github.com/yourusername/EmployeeTaskManagementSy.git
cd EmployeeTaskManagementSy
```

### **2️⃣ Set Up Anaconda Environment**
```sh
conda create --name task_management_env python=3.8
conda activate task_management_env
```

### **3️⃣ Install Dependencies**
```sh
pip install -r requirements.txt
```

### **4️⃣ Configure Database**
```sh
python manage.py makemigrations
python manage.py migrate
```

### **5️⃣ Create Admin Superuser**
```sh
python manage.py createsuperuser
```

### **6️⃣ Collect Static Files**
```sh
python manage.py collectstatic
```

### **7️⃣ Run the Development Server**
```sh
python manage.py runserver
```
Access the application at: **http://127.0.0.1:8000/**

## 🐳 Deployment with Minikube, Kubernetes & Podman

### **1️⃣ Install Required Tools**
- **Enable WSL:** [Install WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- **Enable Hyper-V:** Run the following command in PowerShell (Admin):
  ```sh
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
  ```
- **Podman:** [Download Podman](https://podman.io/getting-started/installation)
- **Minikube:** [Install Minikube](https://minikube.sigs.k8s.io/docs/start/)
- **Kubernetes CLI:** Install via Chocolatey:
  ```sh
  choco install kubernetes-cli -y
  ```

### **2️⃣ Initialize Podman Machine**
```sh
podman machine init
podman machine init --name employee-task-machine --cpus 2 --memory 2200 --disk-size 20
podman machine start employee-task-machine
```

### **3️⃣ Build and Export Docker Image as TAR**
```sh
cd EmployeeTaskManagementSy
podman build -t employeetaskmanager:latest .
podman save -o employeetaskmanager.tar employeetaskmanager:latest
```

### **4️⃣ Load TAR File into Minikube**
```sh
minikube start --driver=docker
minikube image load employeetaskmanager.tar
minikube ssh
docker images | grep employeetaskmanager
```

### **5️⃣ Deploy to Kubernetes**
Apply the deployment:
```sh
kubectl apply -f deployment.yaml
```
Verify the deployment:
```sh
kubectl get pods
kubectl get services
```
Access the application:
```sh
minikube service employee-task-app --url
```

## ℹ️ Additional Information
- **Technologies Used:** Python, Django, Matplotlib, Anaconda, Minikube, Kubernetes, Podman
- **License:** © [Gajal Rathore, Kushi Verma, Darshana Partidar, Ashmeet Singh]. Usage permitted with consent.

## 💎 Alternative Setup (Without Podman)
If you want to deploy directly using Docker instead of Podman:

### **1️⃣ Install Docker & Minikube**
- [Download Docker](https://www.docker.com/get-started/)
- [Install Minikube](https://minikube.sigs.k8s.io/docs/start/)

### **2️⃣ Build and Load Image into Minikube**
```sh
docker build -t employeetaskmanager:latest .
minikube image load employeetaskmanager:latest
```

### **3️⃣ Deploy to Kubernetes**
Apply the deployment:
```sh
kubectl apply -f deployment.yaml
```
Check the deployment:
```sh
kubectl get pods
kubectl get services
```


