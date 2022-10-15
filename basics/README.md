# Sample Kubernetes Cluster
<!-- Create a simple k8 cluster -->
1. Create a index.html.
2. make Dockerfile & add below code.

    ```bash
    FROM nginx:1.17.9 # is the base image
    EXPOSE 80 # export at port 80
    COPY index.html /usr/share/nginx/html # copies .html file where nginx can read & serve it.
    CMD [ "nginx","-g","daemon off;" ] # launches the nginx process without making it background process
    ```

3. Build the docker image.

    ```bash
    docker built -t app .
    ```

4. run the Docker image.

    ```bash
    docker run -ti --rm -p 8080:80 app
    # export port to 80 which is the default port for nginx
    # open browser & visit http://localhost:8080/ 
    ```

5. install minikube & kubectl.

    ```bash
    $ curl -s \
    https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    $ sudo tee /etc/apt/sources.list.d/kubernetes.list > /dev/null <<EOF
    deb http://apt.kubernetes.io/ kubernetes-xenial main
    EOF
    $ sudo apt-get update
    $ sudo apt-get install kubectl
    $ curl -Lo minikube \
    https://storage.googleapis.com/minikube/releases/v1.7.2/minikube-linux-amd64
    $ kubectl get nodes
    $ kubectl run nginx-test \
    --image=nginx \
    --port=80 \
    --restart=Never
    $ kubectl get pods
    $ kubectl expose pods nginx-test --type=NodePort
    $ minikube service nginx-test
    $ kubectl delete service nginx-test
    $ kubectl delete pod nginx-test
    $ minikube stop

    minikube start
    $ minikube start
    $ minikube docker-env
    # execute the o/p of above command to connect minikube docker deamon
    $ docker ps
    $ docker build -t app .
    $ docker images | grep app

    $ kubectl run app \
    --restart=Never \
    --image=app \
    --port=80 \
    --image-pull-policy=IfNotPresent
    $ kubectl get pods
    $ kubectl expose pod app --port=80 --type=NodePort
    $ kubectl get services
    $ minikube service --url app
    $ kubectl get pods

    The Pod object has a collection of properties describing details
    such as:
    • The container image and port.
    • The name and label assigned to the Pod.
    • The server where the Pod should be deployed.

    # You can retrieve the details of the
    with: app Pod
    $ kubectl get pod app -o yaml

    When you ran kubectl expose pod app it created a Service object. Services are similar to load balancers and are used to distribute traffic to Pods.

    Services have properties too, such as:
    • The port exposed to external traffic.
    • The protocol used by the port, such as TCP or UDP.
    • The CNAME record for the current service.

    You can retrieve the details of the Service app with:
    $ kubectl get service app -o yaml

    # You can retrieve the Pod in JSON format with:
    $ kubectl get pod app -o json
    $ kubectl get service app -o json

    $ kubectl explain pod.spec.containers
    ```
