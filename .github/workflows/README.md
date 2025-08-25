## Explaining the Action file
---

### Trigger
 The pipeline is triggered whenever the changes is pushed to the following main branch


### Runner
 The pipline is executed on the git-hub's own runner `Ubuntu:latest`
 

### Code checkout and Docker authentication
- CODE CHECKOUT
    -- The code is checked out using the official github action `actions/checkout@v3`
- Docker creds and authentication
    -- The docker login credentials are stored in the github secrets
    -- Same like the code checkout the action from docker's official `docker/login-action@v2` is used.
    -- The secrets are used in the pipeline code such as secrets.DOCKER_USERNAME, secrets.DOCKER_TOKEN



### Build and Pushing of images to the docker-hub
The same command used in the Docker CLI is used here too.
#### Building
    -  docker build -t ${{ secrets.DOCKER_USERNAME }}/mean:(backend/frontend) ./crud-dd-task-mean-app-2/(backend/frontend)

#### Pushing the image
    -  docker push ${{secrets.DOCKER_USERNAME }}/mean:(backend/frontend) 