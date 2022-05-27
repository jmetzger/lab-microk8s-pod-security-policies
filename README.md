# [LAB] microk8s with pod security policies

## Introduction

This laboratory is developed to have a first contact with the [`Pod Security Policies`](https://kubernetes.io/docs/concepts/policy/pod-security-policy/) locally using [`microk8s`](https://microk8s.io/).

## Important 

This is a a fork of https://githb.com/intelygenz/lab-microk8s-pod-security-policies, because it was set readonly and did not work properly.
Currently it is tested for microk8s 1.23. 

It will NOT work with > 1.23, because it assumes, that secrets are created when creating service accounts, that's not the case 
in microk8s 1.24 anymore.

Also refer to:
https://itnext.io/big-change-in-k8s-1-24-about-serviceaccounts-and-their-secrets-4b909a4af4e0


## LAB assumptions and requirements

This lab assumes you have basic knowledge about [kubernetes](https://kubernetes.io/), [RBAC](https://en.wikipedia.org/wiki/Role-based_access_control) and basic linux commands and concepts.
As a requirement, you must have installed [*(default installation)* `microk8s`](https://microk8s.io/docs/) on your linux PC. Then enable the `dns and the rbac` microk8s plugin: `microk8s.enable dns rbac`.

To check that `microk8s` is running correctly, execute the following command, you should have an output like the one shown below:

```bash
$ sudo microk8s.inspect
Inspecting services
  Service snap.microk8s.daemon-docker is running
  Service snap.microk8s.daemon-apiserver is running
  Service snap.microk8s.daemon-proxy is running
  Service snap.microk8s.daemon-kubelet is running
  Service snap.microk8s.daemon-scheduler is running
  Service snap.microk8s.daemon-controller-manager is running
  Service snap.microk8s.daemon-etcd is running
  Copy service arguments to the final report tarball
Inspecting AppArmor configuration
Gathering system info
  Copy network configuration to the final report tarball
  Copy processes list to the final report tarball
  Copy snap list to the final report tarball
  Inspect kubernetes cluster

Building the report tarball
  Report tarball is at /var/snap/microk8s/383/inspection-report-20190123_110858.tar.gz
```

## Guide

- [1. Configure RBAC](./1.Configure-RBAC.md)
- [2. Create a cluster-admin kubeconfig file](./2.Create-cluster-admin-kubeconfig.md)
- [3. Create an user space](./3.Create-user-space.md)
- [4. Expose secure API Server](./4.Expose-secure-api-server.md)
- [5. Modify kubeconfig files to use secure servers](./5.Modify-kubeconfig-secure-server.md)
- [6. Enable Pod Security Policies](./6.Enable-Pod-Security-Policy.md)
- [7. Configure default Pod Security Policy](./7.Configure-default-pod-security-policy.md)
- [8. Configure kube-system Pod Security Policy](./8.Configure-kube-system-pod-security-policy.md)

## Notes

This is a laboratory and therefore may not function properly. It is designed to show the capabilities offered by pod security policies.
Following this laboratory is enough to know at a high level the functionality of them.

## Based on

- https://joshrosso.com/posts/setting-up-psps
