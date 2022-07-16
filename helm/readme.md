
# install helm
```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod +x get_helm.sh
./get_helm.sh
```

# basic commands
```bash
helm repo list
helm repo add <name> <url>
heml repo remove <name>
heml search repo <chart_name>
heml show <values|chart|readme|all>
helm install <release name> <chart name>
helm install mychart stable/tomcat --wait --timeout 10s
helm create <chart name>
helm delete <chart_name>
helm install mychart  --dry-run stable/tomcat
helm install mychart stable/tomcat --set service.type=NodePort
helm get manifest mychart
helm status <chart_name>
helm pull stable/tomcat --untar
```
