# Helm Kubernetes
Helm is for packaging and deploying kubernetes applications

### Install 

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

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

### To deploy helm package with custom release name
If you do not mention name, helm chooses random names for release, if you want to have custom name for a relase, run the following command
```
  helm install --name my-release nodeapp-helm
```
## NOTE - If you get error as follows when you run above command 
```
configmaps is forbidden: User "system:serviceaccount:kube-system:default" cannot list resource "configmaps" in API group "" in the namespace "kube-system"
```
###  deploy tiller service account RBAC to avoid above error
```
  kubectl --namespace kube-system create serviceaccount tiller
  kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
  kubectl --namespace kube-system patch deploy tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}' 
```

### Upgrade helm release
``` helm upgrade --set-string image.tag=v2 <release-name> <chart-path> ```
```
  helm upgrade --set-string image.tag=v2 nodeapp nodeapp
  
```

### To list out helm releases which are in deployed state
```
  helm ls
```

### To list out helm releases which are deployed and deleted state
```
  helm ls --all
```
### To delete helm release
To delete release completely run following two commands
```
  helm delete helm-release-name

```
