Overview
The Spring PetClinic REST API is a Java Spring Boot backend for managing veterinary clinics, allowing CRUD operations for owners, pets, veterinarians, and visits. It includes a GitHub Actions CI/CD pipeline for automating builds, testing, Dockerization, and deployment.

Tech Stack
Java 17 – Backend framework
Spring Boot 3 – REST API development
Spring Data JPA – ORM for database management
Maven – Build automation
H2 Database – In-memory development database
Docker – Containerization for deployment
GitHub Actions – CI/CD pipeline automation

Setup & Run Locally
1️⃣ Clone the Repository
bash
Copy
Edit
git clone https://github.com/spring-petclinic/spring-petclinic-rest.git
cd spring-petclinic-rest
2️⃣ Build the Project
bash
Copy
Edit
mvn clean install
3️⃣ Run the Application
bash
Copy
Edit
mvn spring-boot:run
API runs at http://localhost:9966/petclinic/api

Dockerizing the Application
1️⃣ Create a Docker Image
bash
Copy
Edit
docker build -t petclinic-api .
2️⃣ Run the Container
bash
Copy
Edit
docker run -p 9966:9966 petclinic-api
CI/CD Pipeline with GitHub Actions
This project includes a GitHub Actions workflow for automating build, test, and deployment steps.

GitHub Actions Workflow (.github/workflows/maven.yml)
yaml
Copy
Edit
name: Java CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      - name: Set up JDK 17
        uses: actions/setup-java@v2
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Build with Maven
        run: mvn clean install

      - name: Build Docker Image
        run: docker build -t petclinic-api .

      - name: Push Docker Image (Optional)
        run: |
          echo "${{ secrets.DOCKER_PASSWORD }}" | docker login -u "${{ secrets.DOCKER_USERNAME }}" --password-stdin
          docker tag petclinic-api your-dockerhub-username/petclinic-api
          docker push your-dockerhub-username/petclinic-api
Screenshots for Submission
📌 Take screenshots of:
✅ GitHub Actions workflow execution (show build success).
✅ Docker build & push logs.
✅ Postman API request & response output.

Contributing
Feel free to fork this repo, make changes, and submit pull requests! 🚀


