# Create Cluster
```
sudo apt update
sudo apt upgrade
sudo vi /etc/hostname # change host name to master or worker
sudo snap install microk8s --classic
microk8s status
sudo snap alias microk8s.kubectl kubectl
kubectl getnodes
```
## On control plane node
```
root@iZ0xi7e9d27kfrlmbodwv2Z:~# sudo microk8s.add-node
From the node you wish to join to this cluster, run the following:
microk8s join 172.16.67.30:25000/0abe75099c063dd8935cb579a928a882/1d888f0ff6c9

Use the '--worker' flag to join a node as a worker not running the control plane, eg:
microk8s join 172.16.67.30:25000/0abe75099c063dd8935cb579a928a882/1d888f0ff6c9 --worker

If the node you are adding is not reachable through the default interface you can use one of the following:
microk8s join 172.16.67.30:25000/0abe75099c063dd8935cb579a928a882/1d888f0ff6c9
```
## On worker node
```
microk8s join <control plane_ip>:<port>/<token>
```
```
root@worker:~# microk8s join 172.16.67.30:25000/b4930111b10350f9af2782d83140fed9/1d888f0ff6c9 --worker
Contacting cluster at 172.16.67.30

The node has joined the cluster and will appear in the nodes list in a few seconds.

This worker node gets automatically configured with the API server endpoints.
If the API servers are behind a loadbalancer please set the '--refresh-interval' to '0s' in:
    /var/snap/microk8s/current/args/apiserver-proxy
and replace the API server endpoints with the one provided by the loadbalancer in:
    /var/snap/microk8s/current/args/traefik/provider.yaml
```
## On control plane node
```
root@iZ0xi7e9d27kfrlmbodwv2Z:~# kubectl get nodes
NAME                      STATUS   ROLES    AGE   VERSION
worker                    Ready    <none>   54s   v1.27.2
master                    Ready    <none>   50m   v1.27.2
```
