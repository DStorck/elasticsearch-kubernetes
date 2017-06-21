# Elasticsearch-Kubernetes
Dockerfile and yamls for elasticsearch deployment on Kubernetes. ElasticSearch is an open source, RESTful search engine built on top of Apache Lucene and released under an Apache license. It is Java-based and can search and index document files in diverse formats.

## Purpose
Static configs for a production grade elasticsearch deploy on kubernetes. This
is also the basis for the helm chart in https://github.com/samsung-cnct/k2-charts/tree/master/elasticsearch

## Architecture details
master nodes:
 - 3 node statefulset
 - if scaled, need to update quorum information

 data nodes:
 - 3 node statefulset
 - scale at will

## Kubernetes Resources
master node (each):
 - 4GB
 - 1/2 CPU (500m)

data nodes (each):
 - 4GB  (first knob to turn up for performance reasons.  Do not exceed 31GB, the jvm breaks down)
 - 1/2 CPU (500m)
 - 20GB of disk (this should be increased greatly for production use)

## How to implement on running Kubernetes cluster
kubectl create -f es.yml


###  [Guide to Elasticsearch Index Performance](https://www.elastic.co/guide/en/elasticsearch/guide/current/indexing-performance.html)
