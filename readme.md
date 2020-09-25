### 

Bienvenido dataclouder, hoy te voy a enseñar como usar kubernetes en Google Cloud, desde lo básico y detallando, todos los pasos, desde  preparar un cluster, conectarte, como subir tu propia aplicación. te muestro un ejemplo con node pero recuerda que siempre lo explico de tal forma que lo puedas adaptar 
a tus necesidades, vamos allá. 


### Demostración de kubernets en la nube

representa al video del tutorial ..


### Intrucciones. 

### Comandos 



### 1) Crear un cluster
```
gcloud container clusters create "mi-cluster2" --num-nodes "2" --disk-size "32" --machine-type "g1-small" --zone "us-central1-c"
```
### 2) Obtener las credenciales del cluster 
    gcloud container clusters get-credentials mi-cluster --zone us-central1-c

### 3) Crear el contenedor. 
    cd nodeapp
    docker build -t gcr.io/[id-projecto]/node-mi-app .

### 3) Subir la imagen a countainer register
    docker push gcr.io/[id-projecto]/node-mi-app

### 4) Crear el despliegue 
    kubectl create deployment node-deplyment --image gcr.io/[project-id]/node-mi-app

### 5) Expone el despligue
    kubectl expose deployment node-deplyment --type=LoadBalancer --port 8080


### Crear objetos de kubernetes con los archivos.

```
# En el archivo app.yaml línea 19 cambia la imagen por la tuya
kubectl apply -f  app.yaml

# Crear el servicio de nodeport 
kubectl apply -f service-node.yaml

# Crear ingress
kubectl apply -f basic-ingress.yaml

```
