# Docker Compose YAML Explanation
---

##  `services:` 
```yaml
services:
```
- Defines all the containers that make up your application
- Each service becomes a separate container when running


---


## Backend Service
```yaml
backend:
  build:
    context: ./backend
  ports:
    - "8080:8080"
  networks:
    - mean-network
```


- Service name is `backend`

`build:`
- Tells Docker Compose to build an image instead of pulling from registry
- `context: ./backend`: Looks for Dockerfile in the `./backend` directory


`ports:`
- Maps container port to host port
- `"8080:8080"`: Maps host port 8080 → container port 8080


`networks:`
- Connects this service to the `mean-network`
- Allows communication with other services on the same network

---

## Frontend Service
```yaml
frontend:
  build:
    context: ./frontend
  ports:
    - "8081:8081"
  networks:
    - mean-network
```

`frontend:`
- Service name for the Angular frontend

`build:`
- `context: ./frontend`: Builds using Dockerfile in `./frontend` directory


`ports:`
- `"8081:8081"`: Maps host port 8081 → container port 8081


`networks:`
- Connected to same network as backend and database

---

## MongoDB Service
```yaml
mongo:
  image: mongo:latest
  networks:
    - mean-network
```

`mongo:`
- Service name 

`image: mongo:latest`
- Uses pre-built latest MongoDB image from Docker Hub

`networks:`
- Connected to same network for database communication


---

## Networks Section
```yaml
networks:
  mean-network:
    driver: bridge
```

**`mean-network:`**
- Name of the network that is gonna be created

`driver: bridge`
- Uses bridge network driver 

---

## Command to start

### Start but terminal is blocked
```bash
docker-compose up
```

### Start in background
```bash
docker-compose up -d
```

### Stop all services
```bash
docker-compose down
```
