# Final Project: Cloud-Native Best Buy Application

* **Name:** Ruaa Thamer
* **Student ID:** 040819157
* **Course:** CST8915 - Cloud Development and Operations
* **Video Demo:** [Link to your YouTube Video]

---

## 1. Architecture Diagram

<img width="3209" height="1782" alt="Architecture Diagram" src="https://github.com/user-attachments/assets/352a0de4-ad49-4110-90c0-4c547fa6df29" />


> **Note:** The diagram above illustrates the decoupled microservices architecture. To ensure **High Availability (Task 2)**, the MongoDB layer is implemented as a **StatefulSet** with 3 replicas and Persistent Volume Claims for data durability.

---

## 2. Brief Application Explanation

This project is a modernized, cloud-native e-commerce solution designed for **Best Buy**. The application has been refactored from the base Algonquin Pet Store template into a specialized electronics retail platform. 

**Key Technical Features:**
* **Microservices:** 5 decoupled services (Store-Front, Store-Admin, Product, Order, Makeline) built with Vue.js, Node.js, and Rust.
* **Data Persistence:** A highly available **MongoDB StatefulSet** with 3 replicas ensures zero data loss and high uptime.
* **Asynchronous Messaging:** **RabbitMQ** manages the order queue, decoupling the Order-Service from the Makeline worker for better scalability.
* **CI/CD Automation:** Full automation using **GitHub Actions** to build, containerize, and push images to Docker Hub upon every commit.

---

## 3. Links Table

| Microservice | GitHub Repository Link | Docker Hub Image Link |
| :--- | :--- | :--- |
| **Store-Front** | https://github.com/RuaaThamer/store-front-best-buy | [ruaa991/bestbuy-store-front:latest](https://hub.docker.com/r/ruaa991/bestbuy-store-front) |
| **Store-Admin** | https://github.com/RuaaThamer/store-admin-best-buy | [ruaa991/bestbuy-store-admin:1.0](https://hub.docker.com/r/ruaa991/bestbuy-store-admin) |
| **Order-Service** | https://github.com/RuaaThamer/order-service-best-buy | [ruaa991/bestbuy-order-service:1.0](https://hub.docker.com/r/ruaa991/bestbuy-order-service) |
| **Product-Service** | https://github.com/RuaaThamer/product-service-best-buy | [ruaa991/product-service-bestbuy:latest](https://hub.docker.com/r/ruaa991/product-service-bestbuy) |
| **Makeline-Service** | https://github.com/RuaaThamer/makeline-service-best-buy | [ruaa991/bestbuy-makeline-service:1.0](https://hub.docker.com/r/ruaa991/bestbuy-makeline-service) |

---

## 4. Deployment Instructions

To deploy the Best Buy stack to an Azure Kubernetes Service (AKS) cluster:

1.  **Connect to AKS Cluster:**
    ```bash
    az aks get-credentials --resource-group [Your-Resource-Group] --name [Your-Cluster-Name]
    ```

2.  **Navigate to Deployment Files:**
    ```bash
    cd Deployment-Files
    ```

3.  **Apply the Manifest:**
    ```bash
    kubectl apply -f aps-all-in-one.yaml
    ```

4.  **Verify Status:**
    ```bash
    kubectl get pods -w
    ```

5.  **Access the Application:**
    Retrieve the External IP for the `store-front` service:
    ```bash
    kubectl get svc store-front
    ```
---

### ⚠️ Important Note on Deployment Environment

Due to my **Azure Student Subscription** being suspended/disabled during the final phase of development, the live deployment on AKS was interrupted. To ensure full project completion and verification, I have taken the following steps:

* **Verification:** I have fully verified the microservices architecture using **local Kubernetes (Docker Desktop)** to prove all service-to-service communication, database persistence, and message queuing are fully functional.
* **Azure Evidence:** I have included screenshots below showing the previously active **AKS Cluster** and the **Subscription Status** to demonstrate that the cloud infrastructure was correctly provisioned and configured.
* **Manifests:** The provided YAML files in the `Deployment-Files/` folder are production-ready and specifically configured for **Azure Kubernetes Service (AKS)** once credits are restored.

---

### Project Evidence & Screenshots

#### 1. Proof of Work (Azure Console)
*The screenshot below shows the AKS cluster and resource group successfully provisioned in my Azure account prior to the suspension.*

<img width="1895" height="911" alt="image" src="https://github.com/user-attachments/assets/62394f13-f82f-4387-87b9-b11a81af45c5" />


#### 2. Technical Hurdle (Subscription Status)
*This screenshot documents the "Account Disabled" status of the student subscription that prevented the final cloud execution.*

<img width="1918" height="565" alt="image" src="https://github.com/user-attachments/assets/0838e636-1fb0-4894-a742-d3f2d4ce7d77" />


#### 3. Local Success (Functional Verification)
*This screenshot shows the Best Buy application running successfully in a local Kubernetes environment, confirming the microservices integration.*

<img width="1917" height="962" alt="image" src="https://github.com/user-attachments/assets/a202608a-30e8-4448-a8ef-e7acb7f56f6b" />


---
