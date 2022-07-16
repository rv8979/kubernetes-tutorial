https://kubernetes.io/docs/tasks/tools/

cluster:



#### run on all vms###########
sudo su
apt-get update
apt-get install apt-transport-https
##################################

##### install docker on all nodes######################
apt install docker.io -y
docker --version
systemctl start docker
systemctl enable docker
##################################################

############ install k8s on all node################################
sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add 
echo "deb http://apt.kubernetes.io/ kubernetes-$(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/kubernetes.list > /dev/null
apt-get update
apt-get install -y kubelet kubeadm kubectl kubernetes-cni
#############################################

#################BOOTSTRAPPING THE MASTER NODE (init maste node)####################
kubeadm init
 

=====if you are tha non root user
mkdir -p $HOME/.kube
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config

==== if you are the root user
export KUBECONFIG=/etc/kubernetes/admin.conf


kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/k8s-manifests/kube-flannel-rbac.yml

#############################################################################################

############################# add node in master ##################
===COPY LONG CODE PROVIDED MY MASTER IN NODE NOW LIKE CODE GIVEN BELOW and run on all slave node

kubeadm join 172.31.6.165:6443 --token kl9fhu.co2n90v3rxtqllrs --discovery-token-ca-cert-hash sha256:b0f8003d23dbf445e0132a53d7aa1922bdef8d553d9eca06e65c928322b3e7c0

######################

##################GO TO MASTER AND RUN THIS COMMAND######################
kubectl get nodes
#####################

