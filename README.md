# Argo-CD-installation-and-more


+++++++++++++++++++++++++++++++++++++++++++++++++++
argo cd:

# install ArgoCD in k8s

kubectl create namespace argocd


kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI

kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd


# login with admin user and below token (as in documentation):


kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo


# you can change and delete init password


# Switch to argodc namespace
# Modify the application.yaml with your git repository and apply to the cluster.

kubectl apply -f application.yaml

# Apply the secret in your cluster. In place of password, use token

kubectl apply -f secrets.yaml

# Push your manifest files to your repo
