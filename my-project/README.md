# 🚀 Strapi Application - Dockerized Setup

This project is a containerized version of a Strapi CMS application using a PostgreSQL database.

---

## 📋 Prerequisites

Before starting, ensure the following tools are installed on your machine:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## 📁 Project Structure

- `Dockerfile` – Defines the environment and commands to run Strapi inside a container  
- `docker-compose.yml` – Manages and runs multiple containers including Strapi and PostgreSQL  
- `package.json` – Contains project dependencies  

---

## ⚙️ Setup Steps

### Step 1: Clone the Repository

Clone the repository to your local machine and navigate into the project directory.

```bash
git clone https://github.com/your-username/your-strapi-project.git
cd your-strapi-project

# 🚀 Strapi Application - Dockerized Setup

This guide will help you containerize a Strapi CMS application with a PostgreSQL database using Docker and Docker Compose.

---

## 🧱 Step 2: Create the `Dockerfile`

Inside the root directory of your Strapi project, create a file named `Dockerfile` with the following instructions:

```Dockerfile
# Use Node.js 18 Alpine as the base image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json yarn.lock ./
RUN yarn install

# Install PostgreSQL node package (if not included)
RUN yarn add pg

# Copy the rest of the application
COPY . .

# Build the Strapi admin panel
RUN yarn build

# Expose port 1337
EXPOSE 1337

# Start the application
CMD ["yarn", "start"]
### 📦 Step 3: Create `docker-compose.yml`

Define services for:

- A **Strapi** container that builds the app and connects to the database
- A **PostgreSQL** container with a predefined database, username, and password
- A **shared volume** to persist PostgreSQL data

Additional configuration:

- Strapi should **depend on the PostgreSQL container**
- Strapi should **map ports** for web access (e.g., `1337:1337`)
### 🛠️ Step 4: Build and Start Containers

Use the Docker Compose command to build the images and start the containers:

```bash
docker-compose up --build

### 🌐 Access the Admin Panel

Once the containers are running, open your browser and visit:

[http://localhost:1337](http://localhost:1337)

Follow the setup instructions to create your first admin user.

---

### 🛑 Shutting Down

To stop and remove the containers, run:

```bash
docker-compose down

