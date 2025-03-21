# argocd-journey

colima start
minikube start

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get pods -A
kubectl port-forward -n argocd svc/argocd-server 8080:443
