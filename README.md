# ARM-Tools
Code Snippets for ARM devices

### Docker Install </br>
curl -sSL https://get.docker.com/ | sh

### K3s Install </br>
#### Server
curl -sLS https://get.k3s.io | INSTALL_K3S_EXEC="server –tls-san "ServerIP" –write-kubeconfig-mode 644" sh –

#### Client
curl -sfL https://get.k3s.io | K3S_URL=https://ServerIP:6443 K3S_TOKEN=$TOKEN sh –
