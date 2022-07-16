sudo -s
apt update
apt install -y curl wget apt-transport-https
apt install -y conntrack
apt install -y docker.io
systemctl enable docker.service
systemctl status docker.service
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
mv minikube-linux-amd64 /usr/local/bin/minikube
chmod +x /usr/local/bin/minikube
minikube version
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version -o yaml
minikube start --driver=none



===============
apt-get install bash-completion
echo 'source <(kubectl completion bash)' >>~/.bashrc