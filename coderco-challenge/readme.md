# Building a Multi-Container Application 🚀  

## Objective  
The goal of this challenge was to create a **multi-container application** using **Docker, Flask, and Redis**. The application consists of:  
- A **Flask web application** that displays a welcome message and tracks visits.  
- A **Redis database** that stores and retrieves the visit count.  
- **Docker and Docker Compose** to containerise and manage both services.  

---

## Process  

### 1️⃣ Building the Flask Application  
First, I created a simple **Flask web application** with two routes:  
- `/` → Displays a welcome message.  
- `/count` → Connects to Redis and increments a visit counter each time the page is accessed.  

Flask is a lightweight Python web framework that makes it easy to build web applications with minimal code.  

---

### 2️⃣ Setting Up Redis  
I used **Redis** as a key-value store to keep track of the visit count. Each time a user visits the `/count` page, Redis stores and updates the count.  

#### 🔹 What is Redis?  
Redis (Remote Dictionary Server) is an **in-memory** database that is often used for caching and real-time analytics. It’s ideal for this project because:  
✅ It’s **lightweight** and fast.  
✅ It **persists data** between requests.  
✅ It can be used as a **cache** to speed up applications.  


---

### 3️⃣ Writing the Dockerfile  
To ensure the **Flask app** runs in a **consistent environment**, I wrote a `Dockerfile` that:  
- Uses a Python base image.  
- Installs Flask and Redis dependencies.  
- Copies the app files into the container.  
- Exposes port **5004** to run the application.  

This makes the app fully containerised, so it can run anywhere without manual setup.  


---

### 4️⃣ Using Docker Compose  
To simplify running multiple containers (**Flask** & **Redis**) together, I used **Docker Compose**. Instead of manually running separate `docker run` commands, Compose allows us to define both services in a `docker-compose.yml` file.  

#### 🔹 Why use Docker Compose?  
- **Simplifies multi-container setups** 🏗️  
- **Automatically manages networking** 🔗  
- **Easier to start/stop the entire application** 🚀  

The `docker-compose.yml` file defines:  
- The **Flask app** (`web`) that depends on Redis.  
- The **Redis service** (`redis`) running in a separate container.  

---

### 5️⃣ Running & Testing the Application  
After setting up everything, I built and ran the containers:  

```sh
docker-compose up --build

![Application Running Screenshot](images/Screenshot%202025-03-16%20at%2010.36.59.png)

