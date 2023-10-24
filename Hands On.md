## Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

## It allows us to define application deployments, configurations, and resources in Git repositories, making it easier to manage and automate Kubernetes applications.

## Here's a basic overview of how to use Argo CD to manage application deployments :-

#### Installing Argo CD :-
##### You can install Argo CD on your Kubernetes cluster using tools like kubectl, Helm, or Kustomize. Here's an example of installing Argo CD using Helm ========>>>>>>>>>>
###### kubectl create namespace argocd
###### helm repo add argo https://argoproj.github.io/argo-helm
###### helm install argocd argo/argo-cd -n argocd
