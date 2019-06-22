# Helm Kubernetes
Helm is for packaging and deploying kubernetes applications


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
### To deploy triller service account RBAC
```
kucbectl create -f https://raw.githubusercontent.com/javahometech/nodeapp-helm/master/rbac/rbac-config.yaml
```
###  deploy triller service account RBAC to avoid above error
```
kucbectl create -f https://raw.githubusercontent.com/javahometech/nodeapp-helm/master/rbac/rbac-config.yaml
```

### To list out helm deployments
```
helm ls
```
### To delete helm deployments
```
helm delete helm-deployment-name
```
