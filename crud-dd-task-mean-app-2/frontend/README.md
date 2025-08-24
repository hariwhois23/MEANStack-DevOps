# Dockerfile explanation

### 1. `FROM node:22-alpine`
```dockerfile
FROM node:22-alpine
```
- Sets the base image for your Docker container

---

### 2. `WORKDIR /usr/src/app`
```dockerfile
WORKDIR /usr/src/app
```
- Creates the directory `/usr/src/app` inside the container
- Sets it as the current working directory
- All the other commands run from this location

---

### 3. `COPY package.json package-lock.json ./`
```dockerfile
COPY package.json package-lock.json ./
```
- Copies both `package.json` and `package-lock.json` from your local machine
- Places them in the current directory (`/usr/src/app`)

---

### 4. `RUN npm install -g @angular/cli && npm install`
```dockerfile
RUN npm install -g @angular/cli && npm install
```
- `npm install -g @angular/cli`
  - Installs Angular CLI globally in the container
  - Provides the `ng` command for building and serving Angular apps
- `npm install`
  - Downloads and installs all dependencies listed in `package.json`
  - Creates `node_modules` folder with project dependencies


---

### 5. `COPY . .`
```dockerfile
COPY . .
```
- Copies all remaining files from your project directory


---

### 6. `EXPOSE 8081`
```dockerfile
EXPOSE 8081
```
- Container listens on port 8081


---

### 7. `CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "8081"]`
```dockerfile
CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "8081"]
```
- Defines the default command to run when container starts


---
