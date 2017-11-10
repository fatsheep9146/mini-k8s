## Vagrant-Based Kubernetes Cluster Ansible Playbook

This playbook is used to start a kubernetes cluster with vagrant. 

This cluster has following features

1. The cluster is composed of two machines, which is master and worker node seperately.
2. Both machines' operating systems are ubuntu 16.04
3. Supported Kubernetes version: 
   - 1.7.2
   - 1.7.5
   - 1.8.0

## How to Prepare for this playbook

In order to use this playbook, you should finish following initializations:

### 1. Install necessary softwares.

Three softwares should be installed

- vagrant: 1.9.2
- virtualbox: 5.1.18
- ansible: 2.2.0

### 2. Download ubuntu 16.04 vagrant box 

$ vagrant box add bento/ubuntu-16.04

## How to Start a new kubernetes cluster

After initialization, you can start a cluster with following steps

```
$ cd path/to/mini-k8s
$ vagrant up

... waiting vagrant up to be done

$ ansible-playbook -i playbook/hosts/vagrant/inventory.yml playbook/deploy.yml

```

## How to Clean up the cluster

When you want to restart the cluster, you should first clean the cluster with following steps.

```
$ cd path/to/mini-k8s
$ ansible-playbook -i playbook/hosts/vagrant/inventory.yml playbook/clean.yml

```

Then you can use deploy.yml to restart the cluster

## How to Destroy the machines

```
$ cd path/to/mini-k8s
$ vagrant destroy -f
```

## How to Control this cluster with kubectl 

You can log into the machine to control kubernetes cluster with kubectl

```
$ cd path/to/mini-k8s
$ vagrant ssh node0
.. After loging into the virtual machine node0 
$ sudo su
$ kubectl get pods -n kube-system
$ others operations with cluster
```


