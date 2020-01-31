# Kubernetes as a Service

On the Cambridge OpenStack system, we are using OpenStack Magnum to provide kubernetes as a Service.
This follows on from the good work done by the CERN OpenStack team. Note that Magnum is now a
[certified kuberenetes installer](https://landscape.cncf.io/selected=magnum)

## WIP: Magnum Examples

More examples on using Magnum can be found in the following code repository:

https://github.com/RSE-Cambridge/iris-magnum

## Accessing my Kubernetes

Once you have access to horizon, you can created a k8s clusters by looking in the "container infra" tab.

Once created, you can access it in this way.

First [install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl):

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
```

Second check you can make use of the OpenStack CLI and python-magnumclient:
```
virtualenv ~/.venv-openstack
. ~/.venv-openstack/bin/activate
pip install -U pip
pip install python-openstackclient python-magnumclient python-heatclient

. openrc
openstack coe cluster list
```

Third pick your cluster name out from the list of clusters above, and do this:

```
eval $(openstack coe cluster config <your-cluster-name-here>)
kubectl version
kubectl cluster-info
kubectl proxy
```
