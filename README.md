**Note:** Make the one worker instance as T2.Xlarge and increase the memory to 20 to 30 gb (you can do this in volumes, increase the volume attached to worker ec2).

**Step1:** 
Install ingress

    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/cloud/deploy.yaml


**Step2:** Clone this repo/ copy files and Run Deployment Manifest 

    kubectl apply -f deployment.yml 
    kubectl apply -f ingress-loadbalancer.yml
    kubectl apply -f route.yml
    
