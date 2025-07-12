#deployment strategy:
1. ReplicaController:
  * A ReplicationController ensures that a specified number of pod replicas are running at any one time. In other words, a ReplicationController makes sure that a pod or a homogeneous set of pods is always up and available.
> vim rc.yml

apiVersion: v1  
kind: ReplicationController  
metadata:  
  name: myapp  
spec:  
  replicas: 10   
  template: 
    metadata: 
      name: xyz 
      labels: 
        app: webserver 
  spec: 
      containers:
        - name: sdfdf 
          image: httpd  
          
> kubectl apply -f rc.yml

2. ReplicaSet:
   * A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. As such, it is often used to guarantee the availability of a specified number of identical Pods.
  > vim rs.yml

apiVersion: apps/v1 
kind: ReplicaSet 
metadata: 
  name: myapp-rs 
spec: 
  replicas: 3 
  selector: 
    matchLabels: 
      app: webserver 
  template: 
    metadata: 
      labels: 
        app: webserver 
    spec: 
      containers: 
        - name: nginx 
          image: nginx  
          
> kubectl apply -f rs.yml

3. Deployment:
   * A Deployment provides declarative updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.  
> vim deployment.yml

apiVersion: apps/v1 
kind: Deployment 
metadata: 
         name: mywebsite 
spec: 
        selector: 
            matchLabels: 
                app: webserver 
       replicas: 5 
       template: 
                metadata: 
                     name: xyz 
                     labels: 
                          app: webserver 
                spec: 
                         containers: 
                                - name: deploy 
                                  image: httpd  
                                  
> kubectl apply -f deployment.yml

    
