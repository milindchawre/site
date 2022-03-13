---
title: "Pluto a Tool to Manage Deprecated Kubernetes Apis"
date: 2022-03-06T18:55:42+05:30
tags: [
    "kubernetes",
    "pluto",
    "nova"
]
categories: [
    "kubernetes"
]
draft: false
---

_This blog was originally featured as a [guide](https://www.civo.com/learn/pluto-a-tool-to-manage-deprecated-kubernetes-apis) in civo cloud community._

![pluto-logo](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/pluto-logo.png)

### Introduction
This guide talks about two tools, Pluto and Nova. But before we dig deeper into the tools themselves, let's first understand why such things are required. For that, we should first understand what is meant by deprecated Kubernetes APIs and why and when we should be concerned about them.


### Kubernetes APIs
The [Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/) is the front-end of the Kubernetes control plane, through which a user interacts with their cluster. Using these APIs, one can query and manipulate [kubernetes objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/) (for example: pods, namespaces, deployments, etc). You can access these Kubernetes APIs [using kubectl or directly through REST api or using client libraries](https://kubernetes.io/docs/tasks/administer-cluster/access-cluster-api/).


### Kubernetes API deprecations or removals
Kubernetes is an API-driven system, whose APIs keep evolving with every new release. The vital part of any API-driven system is having a good API deprecation policy, which informs users if an API is going to be removed or changed. The same is the case with Kubernetes: it periodically reorganizes or upgrades APIs as it evolves. As a result, the old APIs are deprecated and eventually removed. Deprecation in this context means marking an API component for eventual removal. It works now, but it is slated to be removed in an upcoming version. You can read more about how Kubernetes deprecates its APIs in the [deprecation policy documentation](https://kubernetes.io/docs/reference/using-api/deprecation-policy/).


### Why should I be concerned about deprecated APIs?
When you define an application configuration, you specify the API version of the Kubernetes object to be used. Whether a simple Kubernetes YAML manifest or Helm chart, the `apiVersion` field identifies the API version of the Kubernetes object. This means that the user or the maintainer of the application should be aware when Kubernetes API versions have been deprecated and in what Kubernetes version they will be removed.

Also if you upgrade your Kubernetes cluster, there are chances that you might encounter deprecated Kubernetes APIs if the version you upgraded to doesn't support them. For example, suppose resources are running on your cluster, which uses an old API version. In that case, likely, your application using that resource might not work if the deprecated API has been removed in the new cluster version.

A very good example would be APIVersion `extensions/v1beta1` of the Ingress Resource, which was removed in v1.22 version of Kubernetes. You would get an error when trying to use such a removed API version in your configuration:
```
Error: UPGRADE FAILED: current release manifest contains removed kubernetes api(s)
for this kubernetes version and it is therefore unable to build the kubernetes
objects for performing the diff. error from kubernetes: unable to recognize "":
no matches for kind "Ingress" in version "extensions/v1beta1"
```

### Where and how Kubernetes APIs are used
This is how you specify API version in your configuration.
```
# Sample configuration taken from: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#creating-a-deployment
---
apiVersion: apps/v1     <------ API Version of the kubernetes object
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
```
You can also check all supported API groups with its version by referring to [official documentation](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.23/#-strong-api-groups-strong-) or using `kubectl` command line tool command `api-versions`:
```
$ kubectl api-versions
admissionregistration.k8s.io/v1
admissionregistration.k8s.io/v1beta1
apiextensions.k8s.io/v1
apiextensions.k8s.io/v1beta1
apiregistration.k8s.io/v1
apiregistration.k8s.io/v1beta1
apps/v1
```


### Challenges in detecting deprecated APIs in your cluster
As mentioned above, there is official documentation from Kubernetes to check [all the deprecated/removed APIs](https://kubernetes.io/docs/reference/using-api/deprecation-guide/). But the real catch here is how to check which all deprecated APIs and which ones of all resources running in your Kubernetes cluster use them. Listing your Kubernetes resources using [kubectl commands](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) might not give you the correct version of API used, as explained in [this issue](https://github.com/kubernetes/kubernetes/issues/58131#issuecomment-356823588). The solution for this is to use a tool named [Pluto](https://github.com/FairwindsOps/pluto).


### Pluto
[Pluto](https://github.com/FairwindsOps/pluto) is a tool developed by [FairwindsOps](https://www.fairwinds.com/) which helps in detecting [deprecated kubernetes APIs](https://kubernetes.io/docs/reference/using-api/deprecation-guide/) used in your code respositories and helm releases.
- **Features:**
    - It lists all APIs that are deprecated or removed, not only for Kubernetes itself, but also for other tools like Istio, Cert Manager, etc:

    ![list-apis](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/list-apis.png)
    - Detects deprecated APIs from your kubernetes configuration files.

    ![dep-yaml](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/dep-yaml.png)
    - Detects deprecated APIs in Helm charts installed on your cluster.

    ![dep-helm](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/dep-helm.png)
    - It can also be used in your [github workflows](https://github.com/FairwindsOps/pluto#github-action-usage), to continuously keep check of deprecated APIs.


### Installation
You can install `Pluto` on your workstation, by downloading [appropriate release](https://github.com/FairwindsOps/pluto/releases). For example, on my Linux machine I used the following commands to download Pluto v5.4.0, extract the compressed file, mark it executable and move it into my /bin/ directory:
```
$ wget https://github.com/FairwindsOps/pluto/releases/download/v5.4.0/pluto_5.4.0_linux_amd64.tar.gz
$ tar -zxvf pluto_5.4.0_linux_amd64.tar.gz
$ chmod +x pluto
$ cp pluto /bin/pluto
```


### Remediation for deprecated APIs - Nova
Let me take an example. In my case this is what got detected after running `pluto detect-helm` on my cluster.

![dep-helm](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/dep-helm.png)
So as per the first line of the output, my cluster is running a Rancher Helm chart which is using `Ingress` resource which is deprecated and also removed in some future Kubernetes release. I can make use of `pluto list-versions` command to check exactly in which kubernetes version the API is deprecated and removed:

![list-api-output](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/list-api-output.png)
As shown above in the output, the `extensions/v1beta1` is deprecated in version `v1.14.0` and was removed in `v1.22.0`. So if my cluster is running on version later or equal to `v1.22.0` then this helm chart will not work properly and I need to replace this deprecated API `extensions/v1beta1` with the new replacement API `networking.k8s.io/v1`.

While replacing, I'll also need to [accordingly make changes](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#ingress-v122) in my deployment configuration. However, this Helm chart is not one I developed, so I would just need to check and upgrade the Helm chart if a newer version is available from the maintainers. Generally, latest Helm charts use stable APIs which are not deprecated. You can run `helm search repo` command which lists the latest available Helm chart with its version, so you can upgrade.

![helm-search](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/helm-search.png)
But if your cluster has lots of Helm charts installed, then doing so for each and every chart is a tedious task. The good thing is that there is a solution for this problem too: Another tool named [nova](https://github.com/FairwindsOps/nova) which is again developed by [FairwindsOps](https://www.fairwinds.com/). Nova scans your cluster for installed Helm charts, then cross-checks them against all known Helm repositories. If it finds an updated version of the chart you're using, or notices your current version is deprecated, it will let you know. By running `nova find` you can get a report of any charts on your cluster:

![nova-find](https://github.com/milindchawre/civo-k8s/raw/master/blog/pluto/images/nova-find.png)
Combining tools like Pluto and Nova will help you detect and remediate deprecated Kubernetes APIs before they pose issues to compatibility and function.


### Conclusion
I hope this guide will help you in dealing with deprecated Kubernetes APIs. If you found this guide useful, let me know on twitter at [@milindchawre](https://twitter.com/milindchawre) or you can connect me on [Linkedin](https://www.linkedin.com/in/milind-chawre).