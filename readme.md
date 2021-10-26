# Information

- https://bit.ly/k8s-obj-s - Survey
- https://slides.com/gutek/k8s-objectivity-2021?token=YcS3uIcF - Slides

# Links and answers from Q&A session at the end

- https://k3s.io/
- https://k0sproject.io/
- https://microk8s.io/
- https://github.com/ahmetb/kubectx - context and namespace switcher
- https://github.com/instrumenta/kubeval - validate yamls
- https://docs.google.com/presentation/d/1TkH8d7yHKc516E7ddtSd1OW_76aBj46AewHiE6hJRsw/edit?usp=sharing - ingress rules
- https://github.com/jcmoraisjr/haproxy-ingress - ingress for HAProxy
- https://stackoverflow.com/a/52713482/248489 - What is a headless service
- https://github.com/zalando/postgres-operator - Postgres operator
- https://hynek.me/articles/docker-signals/ - Why Your Dockerized Application Isn’t Receiving Signals
- https://linuxhandbook.com/sigterm-vs-sigkill/ - SIGTERM vs SIGKILL: What's the Difference?
- https://intl.cloud.tencent.com/document/product/457/38413 - canary on ingress
- https://docs.microsoft.com/en-us/azure/key-vault/general/key-vault-integrate-kubernetes - KeyVault in K8s
- https://github.com/kubernetes-sigs/secrets-store-csi-driver - driver that let you have keyvault
- https://www.vaultproject.io/docs/platform/k8s - vault

# Some Common Questions

## How to resize volume?

This is possible from version 1.11 (https://kubernetes.io/blog/2018/07/12/resizing-persistent-volumes-using-kubernetes/). Basically StorageClass needs to have `allowVolumeExpansion` set to `true` if it does, we can update PVC (`PersistentVolumeClaim`) to request more storage for POD. However, we need to delete pod. There is another flag `ExpandInUsePersistentVolumes` that needs to be enabled in cluster to allow "dynamic resizing" of volume while pod is running. 

## How exactly networking works in POD and Cluster?

I think this is quite good description with some nice animations: https://itnext.io/an-illustrated-guide-to-kubernetes-networking-part-1-d1ede3322727

There is more to it, network between containers in POD is provided by special kind of container that is named `pause`, more info about this:
https://www.ianlewis.org/en/almighty-pause-container
https://itnext.io/kubernetes-networking-behind-the-scenes-39a1ab1792bb