# VerticalPodAutoscaler
#### [Vertical Pod Autoscaler](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler)
#### [VPA Practice](https://haereeroo.tistory.com/25)
## Prerequisite
* **kubectl** should be connected to the cluster you want to install VPA in.
* **The metrics server** must be deployed in your cluster. 
## Install command

To install VPA, please download the source code of VPA (for example with git clone https://github.com/kubernetes/autoscaler.git) and run the following command inside the vertical-pod-autoscaler directory:
```
./hack/vpa-up.sh
```
