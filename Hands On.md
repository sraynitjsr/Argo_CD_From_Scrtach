## Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

## It allows us to define application deployments, configurations, and resources in Git repositories, making it easier to manage and automate Kubernetes applications.

## Here's a basic overview of how to use Argo CD to manage application deployments :-

####   1. Installing Argo CD :-
#####  We can install Argo CD on our Kubernetes cluster using tools like kubectl, Helm, or Kustomize. Here's an example of installing Argo CD using Helm ========>>>>>>>>>>
###### kubectl create namespace argocd
###### helm repo add argo https://argoproj.github.io/argo-helm
###### helm install argocd argo/argo-cd -n argocd

####   2. Access the Argo CD Web UI :-
#####  Once Argo CD is installed, we can access the web UI by port-forwarding the Argo CD server to local machine ========>>>>>>>>>>
###### kubectl port-forward svc/argocd-server -n argocd 8080:443
###### Open web browser and go to https://localhost:8080. The default login credentials are:
###### Username: admin
###### Password: Retrieve the initial admin password using:
###### kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

#### 3. Define Applications :-
#####   In Argo CD, we define our applications as Kubernetes custom resources (CRs). We can define an application by creating a YAML file like this ========>>>>>>>>>>

apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: my-app
spec:
  destination:
    namespace: my-namespace
    server: https://kubernetes.default.svc
  project: default
  source:
    repoURL: https://github.com/sraynitjsr/<repo>
    targetRevision: HEAD
    path: my-app
  syncPolicy:
    automated:
      prune: true
      selfHeal: true

#### 4. Apply Configuration :-
#####   Apply the application configuration to Argo CD using the kubectl command ========>>>>>>>>>>
######  kubectl apply -f my-app.yaml

#### 5. Sync Applications :-
#####   Once our application is defined, we can sync it using the Argo CD UI or the kubectl command ========>>>>>>>>>>
######  argocd app sync my-app

