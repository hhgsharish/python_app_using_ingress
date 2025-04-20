**Note:** 

> Make the one worker instance as T2.Xlarge and increase the memory to 20 to 30 gb (you can do this in volumes, increase the volume attached to worker ec2).

> This will work with the images I have pushed to the docker hub. 

**Step1:** 
Install ingress

    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/cloud/deploy.yaml


**Step2:** Clone this repo/ copy files and Run Ingress LB Manifest 

    kubectl apply -f ingress-loadbalancer.yml

Once the load balancer is provisioned, copy the external ip/url and paste it in the deployment manifest and apply. 

    kubectl apply -f deployment.yml 

Apply route.yml

    kubectl apply -f route.yml
    
