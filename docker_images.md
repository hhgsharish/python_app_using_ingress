
**Step1:** Checkout the repo 
    
    cd python-reach-sample/api-server-flask/

build image:
    
    docker build -t hhgsharish/python-reach-backend:latest . 

**Step2:**
    
    cd python-reach-sample/react-ui
    
    docker build -t hhgsharish/python-reach-frontend:latest . 
    
**Step3:** 
    
    Push images to docker hub

**docker login**
    
    docker login -u <docker-hub-username>
    
    docker push <docker-hub-username>/python-reach-backend:latest
    docker push <docker-hub-username>/python-reach-frontend:latest

    
    Ex:
    docker push hhgsharish/python-reach-backend:latest
    docker push hhgsharish/python-reach-frontend:latest
