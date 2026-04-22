# Final Project: Cloud-Native Best Buy Application

* **Name:** Ruaa Thamer
* **Student ID:** 040819157
* **Course:** CST8915 - Cloud Development and Operations
* **Video Demo:** [Link to your YouTube Video]

---

## 1. Architecture Diagram

![Best Buy Architecture Diagram](./architecture-diagram.png)

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
| **Store-Front** | [GitHub Repo](https://github.com/RuaaThamer/store-front) | [ruaa991/bestbuy-store-front:latest](https://hub.docker.com/r/ruaa991/bestbuy-store-front) |
| **Store-Admin** | [GitHub Repo](https://github.com/RuaaThamer/store-admin) | [ruaa991/bestbuy-store-admin:1.0](https://hub.docker.com/r/ruaa991/bestbuy-store-admin) |
| **Order-Service** | [GitHub Repo](https://github.com/RuaaThamer/order-service) | [ruaa991/bestbuy-order-service:1.0](https://hub.docker.com/r/ruaa991/bestbuy-order-service) |
| **Product-Service** | [GitHub Repo](https://github.com/RuaaThamer/product-service-bestbuy) | [ruaa991/product-service-bestbuy:latest](https://hub.docker.com/r/ruaa991/product-service-bestbuy) |
| **Makeline-Service** | [GitHub Repo](https://github.com/RuaaThamer/makeline-service) | [ruaa991/bestbuy-makeline-service:1.0](https://hub.docker.com/r/ruaa991/bestbuy-makeline-service) |

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
