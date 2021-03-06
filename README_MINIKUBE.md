## How to start the Demo project with all services in the Minikube

Download repository if you don't have:
`git clone https://github.com/Kv-062-DevOps/post_conv_jtoy.git`

YAML configuration files for Kubernetes contain in the `kube` directory.  

Open the folder **`post_conv_jtoy`** in commandline console and execute:
```
minikube start
kubectl apply -f kube/demo-namespace.yaml
kubectl apply -f kube/db-kube.yaml
kubectl apply -f kube
```
**Important notice**. There are no separate files to create DB and load data. 
All initiations applied in one Backend config (`back-kube.yaml`), section _**initContainers**_.

If something wrong because it started in random order - just try again  
`kubectl apply -f kube`

After that open in your web browser link from command
`minikube service front-srv -n demo --url`
(for example, <http://172.17.0.2:30808>).  

---
To visit a Kubernetes WEB dashboard, use command **`minikube dashboard`**

If you want to see a raw data in the GET service, use:
`minikube service get-srv -n demo --url`
for example, link will be <http://172.17.0.2:30593>

If you want to see a raw data in the Backend service, get the address using command:
`minikube service back-srv -n demo --url`
and open this link in browser, adding a path `/list`, for example: <http://172.17.0.2:31486/list>

### Clear resources after work:
```
kubectl config set-context --current --namespace=demo

kubectl delete deployments back get post db front
kubectl delete services back-srv get-srv post-srv db-srv front-srv 
 
kubectl get pods
kubectl get services
kubectl get services
 
kubectl config set-context --current --namespace=default
 
minikube stop

```
___












