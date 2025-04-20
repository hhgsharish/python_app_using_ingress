
**Step1:** Checkout the repo and Build Backend Image

    git clone https://github.com/devopsdec24/python-reach-sample.git
    cd python-reach-sample/api-server-flask/


**Use this Dockerfile**

        # pull official base image
        FROM node:14-alpine
    
        # set working directory
        WORKDIR /app
        
        # add `/app/node_modules/.bin` to $PATH
        ENV PATH /app/node_modules/.bin:$PATH
        ENV BACKEND_SERVICE "http://123"
        
        # install app dependencies
        COPY package.json ./
        RUN npm install --silent
        RUN npm install react-scripts@4.0.0 -g --silent
        
        # add app
        COPY . ./
        
        # Expose port
        EXPOSE 3000
        
        # start app
        CMD ["npm", "start"]


**build image:**
    
    docker build -t <docker-hub-username>/python-reach-backend:latest . 
    Ex: 
    docker build -t hhgsharish/python-reach-backend:latest . 

**Step2:** Build Front End Image

Modify the config file  to have the backend service ip in "python-reach-sample/react-ui/src/config.js":

![image](https://github.com/user-attachments/assets/87414b9a-bddc-4491-8458-f725c7f842c3)

        let BACKEND_SERVER = null;
        console.log(process.env.BACKEND_SERVICE);
        BACKEND_SERVER = process.env.BACKEND_SERVICE;
        
        const config = {
            // basename: only at build time to set, and don't add '/' at end off BASENAME for breadcrumbs, also don't put only '/' use blank('') instead,
            // like '/berry-material-react/react/default'
            basename: '',
            defaultPath: '/dashboard/default',
            fontFamily: `'Roboto', sans-serif`,
            borderRadius: 12,
            API_SERVER: BACKEND_SERVER
        };

        export default config;

**Build image**
    cd python-reach-sample/react-ui
    docker build -t <docker-hub-username>/python-reach-frontend:latest . 
    Ex: 
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
