**Equipo 2**
# Práctica 2 
### Primera Parte

| Integrante | User | Tarea |
|---------------|-------|---------|
| Ana | @AnaTorresR | (pendiente) |
| Iván | @IvanSalgadoVel |  (pendiente) |
| Dira | @diramtz | (pendiente) |
| León| | (pendiente)|


### [Minikube y AWS](https://github.com/ITAM-DS/analisis-numerico-computo-cientifico/wiki/1.1.Configuracion-de-servicios-basicos-para-uso-de-AWS)

Assumptions: vpc, security groups, .pem key, role must be configured and created. See: [1.1.Configuracion de servicios basicos para uso de AWS]()


**First step**

Select AMI: `opt2-aws-educate-17-03-2021`

`Select m5.2xlarge`


**Second step**

Use next bash script in User data:

``
#!/bin/bash
##variables:
region=us-east-1 #make sure instance is in Virginia
name_instance=minikube
##System update
apt-get update -yq
##Tag instance
INSTANCE_ID=$(curl -s http://instance-data/latest/meta-data/instance-id)
PUBLIC_IP=$(curl -s http://instance-data/latest/meta-data/public-ipv4)
aws ec2 create-tags --resources $INSTANCE_ID --tag Key=Name,Value=$name_instance-$PUBLIC_IP --region=$region

``
**Third step**

ssh to instance:

``ssh -o ServerAliveInterval=60 -i <your key> admin@<ipv4 of ec2 instance>``

->Enable port 22 in security groups

**Fourth step**

Change to root:

``sudo su``

Deploy minikube:

``cd /root && minikube start --driver=none``

**Fifth step**

Deploy kubeflow

``cd /opt/kf-educate && /root/kfctl apply -V -f kfctl_k8s_istio.v1.0.2.yaml``

After 3 mins check with

``kubectl get pods -n kubeflow``

all must be with status "Running" (and one with "Completed")

To access kubeflow UI set:

``
export INGRESS_HOST=$(minikube ip)
export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')

``
Retrieve port

``echo $INGRESS_PORT``

(it's probable that the port will be 31380)

And go to:

``http://<ipv4 of ec2 instance>:$INGRESS_PORT``

->Enable port ``$INGRESS_PORT in security groups
