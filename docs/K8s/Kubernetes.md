# Débuter avec Kubernetes

### Qu'est-ce que Kubernetes ?

Kubernetes, souvent appelé K8s, est un outil open-source conçu pour simplifier la gestion d'applications conteneurisées à grande échelle. Il automatise le déploiement, la mise à l'échelle et la gestion de ces applications, facilitant ainsi le travail des équipes de développement et des opérations.

### Composants principaux de Kubernetes :
Kubernetes se compose de plusieurs composants clés, chacun jouant un rôle spécifique dans la gestion des applications conteneurisées :


1. **Master Node (nœud maître)** :
   - **kube-apiserver** : Le point d'entrée de l'API Kubernetes, traitant les requêtes d'API.
   - **etcd** : Une base de données distribuée pour stocker la configuration et l'état du cluster.
   - **kube-scheduler** : Sélectionne les nœuds appropriés pour le déploiement des pods.
   - **kube-controller-manager** : Gère les contrôleurs pour maintenir l'état du cluster.

2. **Nodes (nœuds)** :
   - **kubelet** : Gère les pods sur un nœud, assurant leur création, leur démarrage, etc.
   - **kube-proxy** : Gère la connectivité réseau pour les pods.

3. **Pods** :
   - L'unité de base contenant un ou plusieurs conteneurs et partageant des ressources.

4. **Controllers** :
   - **Deployment Controller** : Gère les déploiements pour la mise à l'échelle et la mise à jour des applications.
   - **ReplicaSet Controller** : Garantit un nombre spécifié de répliques de pods.
   - **StatefulSet Controller** : Pour les applications nécessitant un stockage persistant.

5. **Services** :
   - Abstrait l'accès aux pods en fournissant une adresse IP stable.

6. **Volumes** :
   - Fournit un stockage persistant pour les données des conteneurs.

7. **Ingress** :
   - Gère les règles de routage HTTP et HTTPS pour exposer les services.

### Premiers pas avec Kubernetes :

#### Installation de Kubernetes localement :

- **Utilisateurs Linux : Minikube**
  - Suivez les instructions sur [le site officiel de Minikube](https://minikube.sigs.k8s.io/docs/start/) pour son installation.

- **Utilisateurs Windows : Docker Desktop**
  - Installez Docker Desktop depuis le [site officiel de Docker](https://www.docker.com/products/docker-desktop).

#### Utilisation de kubectl :

Interagissez avec Kubernetes via `kubectl`, l'interface en ligne de commande, en utilisant des commandes comme :
- `kubectl get nodes` : Affiche les nœuds du cluster.
- `kubectl get pods` : Liste les pods.

#### Déploiement d'une application simple :

Déployons une application web basique avec Nginx à l'aide du fichier `nginx-deployment.yaml`.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx-container
        image: nginx:latest
        ports:
        - containerPort: 80
```

Utilisez kubectl apply -f nginx-deployment.yaml pour créer ce déploiement.

Vérification de l'état de l'application :
Vérifiez l'état du déploiement avec kubectl get pods et obtenez des détails avec kubectl describe deployment nginx-deployment.

Accès à l'application :
Exposez l'application Nginx en créant un service Kubernetes avec le fichier nginx-service.yaml.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: NodePort

```
Appliquez ce fichier YAML avec kubectl apply -f nginx-service.yaml.

Ce guide offre une introduction simple à Kubernetes, détaillant ses composants principaux et fournissant des instructions pour démarrer avec l'installation, l'utilisation de kubectl et le déploiement d'une application Nginx de base.