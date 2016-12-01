# elasticsearch-kubernetes
docker file and yamls for kubernetes deploys

##  purpose
static configs for a production grade elasticsearch deploy on kubernetes. this 
is also the basis for the helm chart in github.com/samsung_cnct/k2-charts

## arch details
master nodes:
 - 3 node pet-set
 - if scaled, need to update quorum information
data nodes:
 - 3 node pet-set
 - scale at will

## kubernetes resources
master node (each):
 - 4GB
 - 1/2 CPU (500m)

data nodes (each):
 - 4GB  (first knob to turn up for performance reasons.  Do not exceed 31GB, the jvm breaks down)
 - 1/2 CPU (500m)
 - 20GB of disk (this should be increased greatly for production use)

## kubernetes requirements
this uses petsets with pvc templates and dynamic persistent volume creation.  This means it needs
a kubernetes version of 1.4.x.  Kubernetes version 1.5.x will not work as the name is changing from
petset to statefulset.  This repo will upgrade after 1.5 goes live.

## how to use
kubectl create -f es.yml