# Dockerfile explanation


### 1. `FROM node:22-alpine`

```dockerfile
FROM node:22-alpine
```
- Sets the base image for your Docker container

---

### 2. `WORKDIR usr/src/app`

```dockerfile
WORKDIR usr/src/app
```

- Creates the directory `/usr/src/app` inside the container
- Sets it as the current working directory
- All subsequent commands run from this location

---

### 3. `COPY package.json .`

```dockerfile
COPY package.json .
```

- Copies `package.json` from your local machine
- Places it in the current directory (`/usr/src/app`)
- The `.` represents the current working directory

---

### 4. `RUN npm install`

```dockerfile
RUN npm install
```

- Executes `npm install` command inside the container
- Downloads and installs all dependencies listed in `package.json`

---

### 5. `COPY . .`

```dockerfile
COPY . .
```

- Copies all remaining files from your project directory
- First `.` = source (your local project folder)
- Second `.` = destination (`/usr/src/app` in container)


---

### 6. `EXPOSE 8080`

```dockerfile
EXPOSE 8080
```

- Container listens on port 8080


---

### 7. `CMD [ "node", "server.js"]`

```dockerfile
CMD [ "node", "server.js"]
```

- Defines the default command to run when container starts
- Starts your Node.js application by running `node server.js`


---

