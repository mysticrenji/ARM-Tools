# ARM-Tools
Code Snippets for ARM devices

### Enable Cgroup </br>
Edit /boot/cmdline.txt and add the following to the end of the line: </br>
cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory

### IPTable Default
sudo update-alternatives --set iptables /usr/sbin/iptables-legacy </br>


### Docker Install </br>
curl -sSL https://get.docker.com/ | sh </br>
curl https://releases.rancher.com/install-docker/19.03.sh | sh

### K3s Install </br>
#### Server
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="server --tls-san "192.168.1.200" --write-kubeconfig-mode 644" INSTALL_K3S_CHANNEL=latest sh -

#### Client
curl -sfL https://get.k3s.io | K3S_URL=https://ServerIP:6443 K3S_TOKEN=$TOKEN sh –

#### Helm 3
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash </br>
kubectl create serviceaccount tiller --namespace kube-system </br>
kubectl create -f tiller-clusterrolebinding.yaml

<pre><code>
#tiller-clusterrolebinding.yaml
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  name: tiller-clusterrolebinding
subjects:
- kind: ServiceAccount
  name: tiller
  namespace: kube-system
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: ""
</pre></code>

#### Install K3s with docker as container runtime </br>
curl -sfL https://get.k3s.io | sh -s - --docker

#### Install K3d </br>
curl -s https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash

#### Install Rust </br>
curl https://sh.rustup.rs -sSf | sh
