# Running Prometheus on GKE 

## Requirements

`kubectl`, `gcloud` and (of course..) [rights to create the RBAC resources in the GKE cluster](https://coreos.com/operators/prometheus/docs/latest/troubleshooting.html)

1. Have access to a GKE cluster with `kubectl`

## Setup (detailed instructions)


### 1. Create the `RBAC` rules 
```
$ kubectl create -f serviceaccount.yaml
$ kubectl create -f roles.yaml
$ kubectl create -f role-bindings.yaml
```

### 2. Create the `configmap` that we're going to mount into the Prometheus `deployment`
```
$ kubectl create -f config-map.yaml
```

### 3. Create the Prometheus `deployment` (with a `persistent volume`)
```
$ kubectl create -f prometheus-deploymemt.yaml
```


### 4. Create the Prometheus Service, exposing the deployment as a `NodePort` 
```
$ kubectl create -f prometheus-service.yaml
```
