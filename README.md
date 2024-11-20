
# Dockerized Simple Web Application

This project demonstrates how to containerize a basic web application using Docker. The app consists of a single HTML file served via Nginx within a Docker container.

---

## **Features**
- Simple web application using an `index.html` file.
- Containerized using Docker for platform independence.
- Uses Nginx to serve the static HTML file.

---

## **Prerequisites**
1. **Docker Desktop** installed and running on your machine.
2. Basic understanding of Docker commands.

---

## **Folder Structure**
```
app/
  └── index.html   # Your HTML application file
Dockerfile          # Instructions to build the Docker image
```

---

## **Dockerfile**
The `Dockerfile` contains the following instructions:
```dockerfile
# Use the official Nginx image
FROM nginx:alpine

# Copy the app folder's content to the default Nginx HTML directory
COPY app /usr/share/nginx/html

# Expose port 80 for the web server
EXPOSE 80

# Start the Nginx server
CMD ["nginx", "-g", "daemon off;"]
```

---

## **Steps to Build and Run the Application**

### **1. Navigate to the Project Directory**
Change to the directory containing the `Dockerfile` and the `app` folder:
```bash
cd path/to/project
```

---

### **2. Build the Docker Image**
Run the following command to build the Docker image:
```bash
docker build -t simple-web-app .
```
- `-t simple-web-app`: Assigns a tag (`simple-web-app`) to the image.
- `.`: Specifies the current directory as the build context.

---

### **3. Run the Docker Container**
Start the Docker container with the following command:
```bash
docker run -d -p 8080:80 simple-web-app
```
- `-d`: Runs the container in detached mode.
- `-p 8080:80`: Maps port 80 in the container to port 8080 on your local machine.
- `simple-web-app`: Name of the Docker image to run.

---

### **4. Access the Web Application**
Open your web browser and navigate to:
```
http://localhost:8080
```
You should see the content of your `index.html` file.

---

### **5. Stop the Docker Container**
To stop the running container:
1. List running containers:
   ```bash
   docker ps
   ```
2. Stop the container using its `CONTAINER ID`:
   ```bash
   docker stop <CONTAINER_ID>
   ```

---

### **6. Clean Up (Optional)**
- To remove the container:
  ```bash
  docker rm <CONTAINER_ID>
  ```
- To delete the Docker image:
  ```bash
  docker rmi simple-web-app
  ```

---

## **Conclusion**
This project showcases how to containerize a simple static web application using Docker and Nginx. You can extend this project by adding more features to your application or customizing the `Dockerfile`.

Happy learning!
