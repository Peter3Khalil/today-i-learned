# Creating Image
1. Create a Dockerfile
2. Build the image

**1.Creating Dockerfile:**
```Dockerfile
FROM node:14
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]
```

**2.Building the image:**
```bash
docker build -t <image-name> .
```


# Running Container
1. Run the container
2. Access the container
3. Stop the container
4. Remove the container
5. Remove the image
6. Start the container

**1.Running the container:**
```bash
docker run -p 3000:3000 -d --name my-container-name <image-name>
```

**2.Access the container:**
```bash
docker exec -it my-container-name /bin/bash
```

**3.Stop the container:**
```bash
docker stop my-container-name
```

**4.Remove the container:**
```bash
docker rm my-container-name
# Example
docker rm my-node-container

# Remove all containers
docker rm $(docker ps -a -q)

# Remove all stopped containers
docker container prune

# Remove all containers and images
docker system prune
```

**5.Remove the image:**
```bash
docker rmi <image-name>
```

**6.Start the container:**
```bash
docker start my-container-name
```
