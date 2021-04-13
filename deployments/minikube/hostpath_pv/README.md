# For Kubeflow namespace next will deploy services:

Set:

```
OPT_LOAD_BALANCER_SERVICE=loadbalancer-opt-0.1-hostpath-pv
OPT_PV=hostpath-pv
OPT_PVC=hostpath-pvc
OPT_JUPYTERLAB_SERVICE=jupyterlab-opt-0.1-hostpath-pv
OPT_URL=https://raw.githubusercontent.com/optimizacion-2-2021-1-gh-classroom/practica-2-primera-parte-diramtz/kubeflow/deployments/minikube/
```

Next lines are not necessary but help to modify services:

```
wget $OPT_URL/hostpath_pv/$OPT_LOAD_BALANCER_SERVICE.yaml
wget $OPT_URL/hostpath_pv/$OPT_PV.yaml
wget $OPT_URL/hostpath_pv/$OPT_PVC.yaml
wget $OPT_URL/hostpath_pv/$OPT_JUPYTERLAB_SERVICE.yaml
```

Create storage:

```
kubectl create -f $OPT_URL/hostpath_pv/$OPT_PV.yaml
kubectl create -f $OPT_URL/hostpath_pv/$OPT_PVC.yaml
```

Create service:

```
kubectl create -f $OPT_URL/hostpath_pv/$OPT_LOAD_BALANCER_SERVICE.yaml
```

Create deployment:

```
kubectl create -f $OPT_URL/hostpath_pv/$OPT_JUPYTERLAB_SERVICE.yaml
```

And after 3 mins go to:
```
http://<ipv4 of ec2 instance>:30001/opturl
```

Delete:

```
kubectl delete service -n kubeflow $OPT_LOAD_BALANCER_SERVICE
kubectl delete pvc -n kubeflow $OPT_PVC
kubectl delete pv -n kubeflow $OPT_PV
kubectl delete deployment -n kubeflow $OPT_JUPYTERLAB_SERVICE 
```

# JUPYTERLAB SERVICE IS USING DOCKER IMAGE FROM NEXT [Dockerfile](https://github.com/optimizacion-2-2021-1-gh-classroom/practica-1-segunda-parte-diramtz/tree/main/dockerfiles)

