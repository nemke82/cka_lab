CKA Lab
=======

Laboratory environment for "Certified Kubernetes Administrator (CKA)" Linux Academy course

kubernetes v1.20 (to use a different version look at https://github.com/pbacterio/cka_lab/tags)

Install VirtualBox 6 minimal to continue.

Build cluster
-------------

Execute: `./build_cluster.sh`

This script creates three virtual machines:

  | name   | IP            |
  | ------ | ------------- |
  | master | 192.168.88.20 |
  | node1  | 192.168.88.21 |
  | node2  | 192.168.88.22 |


To access this machines just use `vagrant ssh <machine>`, for example:

  `vagrant ssh master` or `vagrant ssh node1`


Access Kubernetes
-----------------

The vagrant user on master node has admin credential for kubernetes.
So you can use kubectl on a easy way.

Example:

```
> vagrant ssh master
Linux master 4.19.0-14-amd64 #1 SMP Debian 4.19.171-2 (2021-01-30) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sat Mar  6 12:39:41 2021 from 10.0.2.2
vagrant@master:~$ kubectl get nodes -o wide
NAME     STATUS   ROLES                  AGE     VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE                       KERNEL-VERSION    CONTAINER-RUNTIME
master   Ready    control-plane,master   14m     v1.20.4   10.0.2.15     <none>        Debian GNU/Linux 10 (buster)   4.19.0-14-amd64   docker://18.9.1
node1    Ready    <none>                 8m53s   v1.20.4   10.0.2.15     <none>        Debian GNU/Linux 10 (buster)   4.19.0-14-amd64   docker://18.9.1
node2    Ready    <none>                 8m44s   v1.20.4   10.0.2.15     <none>        Debian GNU/Linux 10 (buster)   4.19.0-14-amd64   docker://18.9.1

```


Shutdown
--------

To stop all the machines execute: `vagrant halt`


Boot up
-------

To boot up the cluster use: `vagrant up`


Destroy
-------

If you want to destroy the cluster to build it again or just to free resources,
use: `vagrant destroy`
