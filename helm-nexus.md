# Configure Nexus Repository for Helm

#### 1. Create Helm Hosted Repository

```
  nexus home --> Settings(Server Administration and Configuration) --> Repositories --> create repository --> helm(hosted) 
  give meaningful name for example "javahomeapp-k8s"
```

#### 2. Integrate helm with nexus repo

```
  helm repo add nexus http://<nexus-username>:<nexus-password>@<nexus-ip>:<nexus-port>/repository/javahomeapp-k8s
```

#### 3. Create sample helm chart

```
  heml create javahomeapp
  
```

#### 4. Package helm chart

```
  heml package javahomeapp
  
```

#### 4. Push helm chart to nexus

```
 curl -v -F file=@javahomeapp-0.1.0.tgz -u admin:admin http://172.31.66.14:8081/service/rest/v1/components?repository=javahomeapp-k8s
 makesure you change above values according to your requirements
  
```

#### 5. Deploy helm chart from nexus

```
  helm install --name nexusdemo nexus/javahomeapp --version 0.1.0
  
```
