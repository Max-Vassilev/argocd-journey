# argocd-journey

colima start

minikube start

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get pods -A

kubectl port-forward -n argocd svc/argocd-server 8080:443

kubectl get secret argocd-initial-admin-secret -n argocd -o yaml

echo PASSWORD | base64 --decode

![image](https://github.com/user-attachments/assets/aad94b9f-e165-4d5b-accf-655a03f17d7b)
