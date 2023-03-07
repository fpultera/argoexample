install minikube
start minikube
    minikube start

delete minikube
    minikube delete --all

Install ingress addon
    minikube addons enable ingress
    kubectl get pods -n ingress-nginx

Test addon
    kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0
    kubectl expose deployment web --type=NodePort --port=8080
    kubectl get service web (obtain ip url for exposed services)

Ingress example
    kubectl apply -f https://k8s.io/examples/service/networking/example-ingress.yaml
    kubectl get ingress (obtain ingress)
    In /etc/host machine add the ip obtained and url

Install ArgoCD
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

Check ArgoCD status
    kubectl get pods -n argocd (if all running, get secret for admin user)
    kubectl get secret -n argocd (get encode secret to argocd-initial-admin-secret object)
    kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode

Login admin in ArgoCD instalation
    kubectl get services -n argocd (check if exist argocd-server services and create port forward for login)


