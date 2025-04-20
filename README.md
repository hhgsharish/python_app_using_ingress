**Note:** 

> Make the one worker instance as T2.Xlarge and increase the memory to 20 to 30 gb (you can do this in volumes, increase the volume attached to worker ec2).

> This will work with the images I have pushed to the docker hub. 

**Step1:** 
Install ingress

    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/cloud/deploy.yaml


**Step2:** Clone this repo/ copy files and Run Ingress LB Manifest 

    kubectl apply -f ingress-loadbalancer.yml
    kubectl get svc -n ingress-nginx
    kubectl get pods -n ingress-nginx
    
![image](https://github.com/user-attachments/assets/aebd4ef8-7595-4063-ada1-abcfa5b4ce4f)

Once the load balancer is provisioned, copy the external ip/url and paste it in the deployment manifest(line 53) and apply. 

    kubectl apply -f deployment.yml 

Apply route.yml

    kubectl apply -f route.yml

This will deploy the app, make sure the backend service works by checking network monitor (get into it by pressing F12), register and log in. 
![image](https://github.com/user-attachments/assets/316fe9f9-f64a-41d6-8c6b-ed337bfca8c0)

![image](https://github.com/user-attachments/assets/c0830f46-ba6a-4025-83c7-27264e233465)




