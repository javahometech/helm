# Helm Kubernetes
Helm is for packaging and deploying kubernetes applications

### Install 

```
curl -LO https://git.io/get_helm.sh
chmod 700 get_helm.sh
./get_helm.sh

```

### To intial helm local repository
```
helm init
```
### To create helm chart
```
helm create nodeapp-helm
```
### To create helm package
```
helm package nodeapp-helm
```
### To deploy helm package
```
helm install nodeapp-helm
```
## NOTE - If you get error as follows when you run above command 

```
configmaps is forbidden: User "system:serviceaccount:kube-system:default" cannot list resource "configmaps" in API group "" in the namespace "kube-system"
```
###  deploy triller service account RBAC to avoid above error
```
kubectl --namespace kube-system create serviceaccount tiller
```
```
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
```
```
kubectl --namespace kube-system patch deploy tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}' 
```

### To list out helm deployments
```
helm ls
```
### To delete helm deployments
```
helm delete helm-deployment-name
```
