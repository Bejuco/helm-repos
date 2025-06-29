# Home Lab Helm Repos
This is a (soon) to be collection of helm repos I'm using on my Kubernetes Home Lab. They try to be as modular as possible, but first of all they work for me. 

## My setup
My Kubernetes cluster is 3x Control Plane/etcd nodes + 2 Worker Nodes of K3S, using **Longhorn** as storage, NFS (on a Synology) for some media storage/access. Oh and Kube-VIP which doesn't affect much, except that is the LB behind Traefik for Ingress. 

All the nodes are VMs on a 5x node cluster, which runs CEPH for HA. That doesn't affect much of the helm usage but It took me a long while and I'm still proud of it. 

### WHy Kubernetes?
I don't know, I still think Kubernetes is like when you over-normalize a DB, but in practice, it's normally rock solid for me, and the few times I had to rebuild, takes me about 25 minutes to rebuild an entire cluster, or just a couple of minutes to replace a non-behaving node. With Docker standalone, I have a single-point-of-failure, and with a cluster of Swarm, troubleshooting that has been a nightmare. Call me old fashion, but when I troubleshoot I like to see something in order to actually troubleshoot. 


## Note on AI
Some of the helm charts, were/Are being built with the help of AI. But rest assured, I run them for a while before publishing. 