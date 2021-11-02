# VerticalPodAutoscaler
#### [Vertical Pod Autoscaler](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler)
#### [VPA Practice](https://haereeroo.tistory.com/25)
## Prerequisite
* **kubectl** should be connected to the cluster you want to install VPA in.
* **[The metrics server](https://github.com/kubernetes-sigs/metrics-server)** must be deployed in your cluster. 
## Install command

To install VPA, please download the source code of VPA (for example with git clone https://github.com/kubernetes/autoscaler.git) and run the following command inside the vertical-pod-autoscaler directory:
```
./hack/vpa-up.sh
```
##Quick start

After installation the system is ready to recommend and set resource requests for your pods. In order to use it you need to insert a Vertical Pod Autoscaler resource for each controller that you want to have automatically computed resource requirements. This will be most commonly a Deployment. There are three modes in which VPAs operate:

"**Auto**": VPA assigns resource requests on pod creation as well as updates them on existing pods using the preferred update mechanism. Currently this is equivalent to "Recreate" (see below). Once restart free ("in-place") update of pod requests is available, it may be used as the preferred update mechanism by the "Auto" mode. NOTE: This feature of VPA is experimental and may cause downtime for your applications.
"**Recreate**": VPA assigns resource requests on pod creation as well as updates them on existing pods by evicting them when the requested resources differ significantly from the new recommendation (respecting the Pod Disruption Budget, if defined). This mode should be used rarely, only if you need to ensure that the pods are restarted whenever the resource request changes. Otherwise prefer the "Auto" mode which may take advantage of restart free updates once they are available. NOTE: This feature of VPA is experimental and may cause downtime for your applications.
"**Initial**": VPA only assigns resource requests on pod creation and never changes them later.
"**Off**": VPA does not automatically change resource requirements of the pods. The recommendations are calculated and can be inspected in the VPA object.
