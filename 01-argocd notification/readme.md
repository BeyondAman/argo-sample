Argo notification with rollouts:

# deploy argocd 
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# install argo cd notification controller
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj-labs/argocd-notifications/release-1.0/manifests/install.yaml

# install notification template
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj-labs/argocd-notifications/release-1.0/catalog/install.yaml






kubectl patch cm argo-rollouts-notifications-cm -n argocd --type merge -p '{"data": {"service.email.gmail": "{ username: tempmail436@gmail.com, password: tempmailpassword, host: smtp.gmail.com, port: 465, from: tempmail436@gmail.com }",
"service.slack": "{ apiURL: <url>, token: xoxb-2219249599776-2228900099952-LoW9o6AN2C3EISnpCdW0VVGC, username: username, icon: icon }"}}'

