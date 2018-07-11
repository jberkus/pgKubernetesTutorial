# pgKubernetesTutorial

This repository will contain the materials for the upcoming pgKubernetes workshop at OSCON 2018.  If you are planning to attend that workshop, there are several things you need to do in order to participate in the hands-on exercises.

*Important: students who want to do the hands-on for the workshop are expected to complete the steps under "preparation" below before the workshop starts.  No time will be given during the workshop to perform these setup steps*

## Preparation

While you are welcome to attend the tutorial without participating in the exercises, you will get more out of it if you do so.  

All of the prepartion steps below should be done on the laptop that you plan to bring to the workshop.  This

### Install MiniKube

We will be performing the exercises on the Minikube VM (or native docker install, on Linux).  Instructions on how to install minikube can be found [on the minikube github](https://github.com/kubernetes/minikube).  You must install:

* minikube
* kubectl
* a VM runtime that supports minikube, if not already present

Instructions for doing all of these for Linux, Windows, and MacOS are [on the minikube github](https://github.com/kubernetes/minikube).

### Start Minikube

In order to make sure that you have all of the data loaded and prepared, you should start minikube.  You may want to wait until a couple days before the workshop to do this, as it will take up space/memory on your laptop.

```
minikube start
```

Many/most students will need to add `--vm-driver` to the above, for whichever VM runtime they have.  Again, instructions and examples for this are [on the minikube github](https://github.com/kubernetes/minikube).

```
minikube start --vm-driver kvm2
Starting local Kubernetes v1.10.0 cluster...
Starting VM...
Getting VM IP address...
Moving files into cluster...
Downloading kubeadm v1.10.0
Downloading kubelet v1.10.0
Finished Downloading kubeadm v1.10.0
Finished Downloading kubelet v1.10.0
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
[jberkus@ariolimax presos]$ kubectl version
Client Version: version.Info{Major:"1", Minor:"11", GitVersion:"v1.11.0", GitCommit:"91e7b4fd31fcd3d5f436da26c980becec37ceefe", GitTreeState:"clean", BuildDate:"2018-06-27T20:17:28Z", GoVersion:"go1.10.2", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.0", GitCommit:"fc32d2f3698e36b93322a3465f63a14e9f0eaead", GitTreeState:"clean", BuildDate:"2018-03-26T16:44:10Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"linux/amd64"}
[jberkus@ariolimax presos]$ minikube cache add registry.opensource.zalan.do/acid/spilo-9.6:1.2-p26
```

Test that it's working:

```
14:10 $ kubectl get nodes
NAME       STATUS    ROLES     AGE       VERSION
minikube   Ready     master    2m        v1.10.0

```

### Cache Container Images

In order to anticipate OSCON's bandwidth, we want to cache the main postgres container image:

```
minikube cache add registry.opensource.zalan.do/acid/spilo-cdp-10:1.4-p8
```

### Suspend minikube

Once minikube is started up, it will have cached a lot of images.  So don't delete the VM.  Instead, halt it with:

```
minikube stop
```

And you should be able to start things at the beginning of the workshop.

### Clone this repository

Switch to a good working directory for the exercises on your machine, and git clone the repository:

```
git clone https://github.com/jberkus/pgKubernetesTutorial.git
```

### Install PSQL

Optionally, you may want to install PSQL on your platform in order to connect with the deployed cluster for testing.  This installation will depend heavily on your OS and version, so we won't cover it here.  Instead, see [the Postgres guide](http://postgresguide.com/setup/install.html).  Note that you only need the "client utilities", and not the database server.

### Problems With Preparation

Problems with any of the above steps?  Please file an issue on this repo and I will respond.
