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
## On control plane node and run the following command to generate a connection string
```
root@iZ0xi7e9d27kfrlmbodwv2Z:~# sudo microk8s.add-node
From the node you wish to join to this cluster, run the following:
microk8s join 172.16.67.30:25000/0abe75099c063dd8935cb579a928a882/1d888f0ff6c9

Use the '--worker' flag to join a node as a worker not running the control plane, eg:
microk8s join 172.16.67.30:25000/0abe75099c063dd8935cb579a928a882/1d888f0ff6c9 --worker

If the node you are adding is not reachable through the default interface you can use one of the following:
microk8s join 172.16.67.30:25000/0abe75099c063dd8935cb579a928a882/1d888f0ff6c9
```
