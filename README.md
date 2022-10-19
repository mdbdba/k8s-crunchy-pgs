# k8s-crunchy-pgs
small k8s cluster to be used for crunchy postgresql demos. Implemented with flux, so to get up and running for yourself:
* fork this repo to one of your own.
* have `k3d` (https://k3d.io/) and `flux` (https://fluxcd.io/flux/installation/) installed.
* when bootstrapping your cluster use the name of your forked repo instead of mine in the repository argument.

Create the cluster
```shell
❯ k3d cluster create --config=k3d.yaml
INFO[0000] Using config file k3d.yaml (k3d.io/v1alpha4#simple) 
INFO[0000] portmapping '8081:80' targets the loadbalancer: defaulting to [servers:*:proxy agents:*:proxy] 
INFO[0000] portmapping '443:443' targets the loadbalancer: defaulting to [servers:*:proxy agents:*:proxy] 
INFO[0000] Prep: Network                                
INFO[0000] Created network 'k3d-crunchy'                
INFO[0000] Created image volume k3d-crunchy-images      
INFO[0000] Starting new tools node...                   
INFO[0000] Starting Node 'k3d-crunchy-tools'            
INFO[0001] Creating node 'k3d-crunchy-server-0'         
INFO[0001] Creating node 'k3d-crunchy-agent-0'          
INFO[0001] Creating node 'k3d-crunchy-agent-1'          
INFO[0001] Creating node 'k3d-crunchy-agent-2'          
INFO[0001] Creating LoadBalancer 'k3d-crunchy-serverlb' 
INFO[0001] Using the k3d-tools node to gather environment information 
INFO[0001] HostIP: using network gateway 172.24.0.1 address 
INFO[0001] Starting cluster 'crunchy'                   
INFO[0001] Starting servers...                          
INFO[0001] Starting Node 'k3d-crunchy-server-0'         
INFO[0007] Starting agents...                           
INFO[0008] Starting Node 'k3d-crunchy-agent-1'          
INFO[0008] Starting Node 'k3d-crunchy-agent-0'          
INFO[0008] Starting Node 'k3d-crunchy-agent-2'          
INFO[0018] Starting helpers...                          
INFO[0018] Starting Node 'k3d-crunchy-serverlb'         
INFO[0025] Injecting records for hostAliases (incl. host.k3d.internal) and for 5 network members into CoreDNS configmap... 
INFO[0028] Cluster 'crunchy' created successfully!      
INFO[0028] You can now use it like this:                
kubectl cluster-info
```

# Boostrap (this'll take a few minutes)
# Remember to use the name of your repo in the repository argument.
```shell
flux bootstrap github \
--owner=$GITHUB_USER \
--repository=k8s-crunchy-pgs \
--branch=main \
--path=./ops \
--personal
```







