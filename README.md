# End to End DevSecOps Project

## Introduction

In the ever-evolving landscape of software development, the integration of security practices into the development and deployment processes has become paramount. DevSecOps, an extension of DevOps, emphasizes the seamless integration of security into the software development lifecycle. This project serves as an exploration of various DevOps and DevSecOps tools, providing hands-on experience with their implementation.

## Tools Covered

- **Linux**: The foundational operating system for hosting our DevOps and DevSecOps tools.
- **Git and GitHub**: Version control system and collaboration platform for managing code repositories.
- **Docker**: Containerization platform used for packaging applications and their dependencies into standardized units.
- **Docker-compose**: Tool for defining and running multi-container Docker applications.
- **Jenkins CI/CD**: Automation server for building, testing, and deploying software continuously.
- **SonarQube Scan**: Static code analysis tool for identifying and fixing code quality and security issues.
- **SonarQube Quality Gates**: Criteria set to ensure code quality and security standards are met before code is deployed.
- **Trivy**: Vulnerability scanner for container images, providing insights into security risks.

## Project Overview

This project focuses on deploying a 3-tier application using Docker and implementing Continuous Integration/Continuous Deployment (CI/CD) pipelines with Jenkins. The emphasis is on incorporating DevSecOps practices throughout the development and deployment process. By following along with this project, you will gain practical experience with each of the covered tools and learn how to seamlessly integrate security into your DevOps workflow.

---

Feel free to explore the sections below for detailed instructions, insights, and hands-on experience with each tool and aspect of the project. Let's dive into the world of DevOps and DevSecOps together!





# Wanderlust - Your Ultimate Travel Blog 🌍✈️


## 🎯 Goal of this project


## Setting up the project locally

### Setting up the Backend

1. **Fork and Clone the Repository**

   ```bash
   git clone https://github.com/{your-username}/wanderlust.git
   ```

2. **Navigate to the Backend Directory**

   ```bash
   cd backend
   ```

3. **Install Required Dependencies**

   ```bash
   npm i
   ```

4. **Set up your MongoDB Database**

   - Open MongoDB Compass and connect MongoDB locally at `mongodb://localhost:27017`.

5. **Import sample data**

   > To populate the database with sample posts, you can copy the content from the `backend/data/sample_posts.json` file and insert it as a document in the `wanderlust/posts` collection in your local MongoDB database using either MongoDB Compass or `mongoimport`.

   ```bash
   mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray
   ```

6. **Configure Environment Variables**

   ```bash
   cp .env.sample .env
   ```

7. **Start the Backend Server**

   ```bash
   npm start
   ```

   > You should see the following on your terminal output on successful setup.
   >
   > ```bash
   > [BACKEND] Server is running on port 5000
   > [BACKEND] Database connected: mongodb://127.0.0.1/wanderlust
   > ```

### Setting up the Frontend

1. **Open a New Terminal**

   ```bash
   cd frontend
   ```

2. **Install Dependencies**

   ```bash
   npm i
   ```

3. **Configure Environment Variables**

   ```bash
   cp .env.sample .env.local
   ```

4. **Launch the Development Server**

   ```bash
   npm run dev
   ```
