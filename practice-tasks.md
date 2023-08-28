## Questions are not from any actual exam!!!



❗: Q:  Create a job that calculates pi to 2000 decimal points using the container with the image named perl
and the following commands issued to the container:  ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
Once the job has completed, check the logs to and export the result to pi-result.txt.

Solution:

kc job pi2000 --image=perl -o yaml --dry-run > pi2000.yaml

### edit the file, edit the name, remove any ID references and include the command argument under container spec.

        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]


aapiVersion: batch/v1
kind: Job
metadata:
  creationTimestamp: null
  name: pi2000
spec:
  template:
    metadata:
      creationTimestamp: null
    spec:
      containers:
      - image: perl
        name: pi2000
        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
        resources: {}
      restartPolicy: Never
status: {}


kc -f pi2000.yaml

### get the output from the logs and export them to text file

gl pi2000-xvrpt > pi-result.txt



❗ Q. Create a yaml file called nginx-deploy.yaml for a deployment of three replicas of nginx, listening on the container's port 80.
They should have the labels role=webserver and app=nginx. The deployment should be named nginx-deploy.
Expose the deployment with a load balancer and use a curl statement on the IP address of the load balancer
to export the output to a file titled output.txt.


Solution:

sudo kubectl run nginx-deploy --labels="role=webserver,app=nginx" --image=nginx --replicas=3 --port=80 -o yaml > nginx-deployment.yaml

### expose the deployment with a loadbalancer type, call it nginx-service

kubectl expose deployment nginx-deploy --type=LoadBalancer --name=nginx-service

### use a curl statement that connects to the IP endpoint of the nginx-service and save the output to a file called output.txt

curl IP > output.txt




❗ Q.  Scale the deployment you just made down to 2 replicas

Solution:

sudo kubectl scale deployment nginx-deploy --replicas=2



❗ Q. Create a pod called "haz-docs" with an nginx image listening on port 80.
Attach the pod to emptyDir storage, mounted to /tmp in the container.
Connect to the pod and create a file with zero bytes in the /tmp directory called my-doc.txt.

Solution:

apiVersion: apps/v1beta1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    run: haz-docs
  name: haz-docs
spec:
  replicas: 1
  selector:
    matchLabels:
      run: haz-docs
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        run: haz-docs
    spec:
      containers:
      - image: nginx
        name: haz-docs
        volumeMounts:
        - mountPath: /tmp
          name: tmpvolume
        ports:
        - containerPort: 80
        resources: {}
      volumes:
      - name: tmpvolume
        emptyDir: {}
status: {}


sudo kubectl exec -it haz-docs-5b49cb4d87-2lm5g /bin/bash

root@haz-docs-5b49cb4d87-2lm5g:/# cd /tmp/
root@haz-docs-5b49cb4d87-2lm5g:/tmp# touch my-doc.txt
root@haz-docs-5b49cb4d87-2lm5g:/tmp# ls
my-doc.txt


❗ Q. Label the worker node of your cluster with rack=qa.

Solution:

sudo kubectl label node texasdave2c.mylabserver.com rack=qa


❗ Q.  Create a file called counter.yaml in your home directory and paste the following yaml into it:

Solution:

apiVersion: v1
kind: Pod
metadata:
  name: counter
spec:
  containers:
  - name: count
    image: busybox
    args: [/bin/sh, -c, 'i=0; while true; do echo "$i: $(date)"; i=$((i+1)); sleep 1; done']

Start this pod.
Once its logs exceed a count of 20 (no need to be precise — any time after it has reached 20 is fine),
save the logs into a file in your home directory called count.result.txt.


❗ Q.
Create a new namespace called "cloud9".
Create a pod running k8s.gcr.io/liveness with a liveliness probe that uses httpGet to
probe an endpoint path located at /cloud-health on port 8080.
The httpHeaders are name=Custom-Header and value=Awesome.
The initial delay is 3 seconds and the period is 3.



❗ Q. Create a deployment with two
cloud_user@k8s-control:~$ nano new-file.txt
cloud_user@k8s-control:~$ vi new-file.txt
cloud_user@k8s-control:~$ cat new-file.txt
## Questions are not from any actual exam!!!



:point_right: Q:  Create a job that calculates pi to 2000 decimal points using the container with the image named perl
and the following commands issued to the container:  ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
Once the job has completed, check the logs to and export the result to pi-result.txt.

Solution:

kc job pi2000 --image=perl -o yaml --dry-run > pi2000.yaml

### edit the file, edit the name, remove any ID references and include the command argument under container spec.

        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]


aapiVersion: batch/v1
kind: Job
metadata:
  creationTimestamp: null
  name: pi2000
spec:
  template:
    metadata:
      creationTimestamp: null
    spec:
      containers:
      - image: perl
        name: pi2000
        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
        resources: {}
      restartPolicy: Never
status: {}


kc -f pi2000.yaml

### get the output from the logs and export them to text file

gl pi2000-xvrpt > pi-result.txt



:point_right: Q. Create a yaml file called nginx-deploy.yaml for a deployment of three replicas of nginx, listening on the container's port 80.
They should have the labels role=webserver and app=nginx. The deployment should be named nginx-deploy.
Expose the deployment with a load balancer and use a curl statement on the IP address of the load balancer
to export the output to a file titled output.txt.


Solution:

sudo kubectl run nginx-deploy --labels="role=webserver,app=nginx" --image=nginx --replicas=3 --port=80 -o yaml > nginx-deployment.yaml

### expose the deployment with a loadbalancer type, call it nginx-service

kubectl expose deployment nginx-deploy --type=LoadBalancer --name=nginx-service

### use a curl statement that connects to the IP endpoint of the nginx-service and save the output to a file called output.txt

curl IP > output.txt




:point_right: Q.  Scale the deployment you just made down to 2 replicas

Solution:

sudo kubectl scale deployment nginx-deploy --replicas=2



:point_right: Q. Create a pod called "haz-docs" with an nginx image listening on port 80.
Attach the pod to emptyDir storage, mounted to /tmp in the container.
Connect to the pod and create a file with zero bytes in the /tmp directory called my-doc.txt.

Solution:

apiVersion: apps/v1beta1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    run: haz-docs
  name: haz-docs
spec:
  replicas: 1
  selector:
    matchLabels:
      run: haz-docs
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        run: haz-docs
    spec:
      containers:
      - image: nginx
        name: haz-docs
        volumeMounts:
        - mountPath: /tmp
          name: tmpvolume
        ports:
        - containerPort: 80
        resources: {}
      volumes:
      - name: tmpvolume
        emptyDir: {}
status: {}


sudo kubectl exec -it haz-docs-5b49cb4d87-2lm5g /bin/bash

root@haz-docs-5b49cb4d87-2lm5g:/# cd /tmp/
root@haz-docs-5b49cb4d87-2lm5g:/tmp# touch my-doc.txt
root@haz-docs-5b49cb4d87-2lm5g:/tmp# ls
my-doc.txt


:point_right: Q. Label the worker node of your cluster with rack=qa.

Solution:

sudo kubectl label node texasdave2c.mylabserver.com rack=qa


:point_right: Q.  Create a file called counter.yaml in your home directory and paste the following yaml into it:

Solution:

apiVersion: v1
kind: Pod
metadata:
  name: counter
spec:
  containers:
  - name: count
    image: busybox
    args: [/bin/sh, -c, 'i=0; while true; do echo "$i: $(date)"; i=$((i+1)); sleep 1; done']

Start this pod.
Once its logs exceed a count of 20 (no need to be precise — any time after it has reached 20 is fine),
save the logs into a file in your home directory called count.result.txt.


:point_right: Q.
Create a new namespace called "cloud9".
Create a pod running k8s.gcr.io/liveness with a liveliness probe that uses httpGet to
probe an endpoint path located at /cloud-health on port 8080.
The httpHeaders are name=Custom-Header and value=Awesome.
The initial delay is 3 seconds and the period is 3.



:point_right: Q. Create a deployment with two
