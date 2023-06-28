# Crucible: OpenShift 4 Management Cluster with Cilium CNI.
This project is an example to build openshift cluster 4.12.x IPI with **Cilium CNI**, My Env have no internet connectivity so i will prepeare my registry with required images on a machine having internet then we will use that registry for this demo..!

* This repository contains playbooks for automating the creation of an OpenShift Container Platform cluster on premise on Virtual and Bare Metal deployments have been tested in restricted network environments where nodes do not have direct access to the Internet.

* This repository contains manifest for installing Cilium CNI which will be used as an patch during cluster installation.

For More information please check official repository link for redhat crucible in documentation section.


## Software Verison used in this Demo

RHEL version :-

`8.6`

Openshift Version :-

`v4.12.4`

Assisted Installer :-

`v2.12.1`


## Deployment

As a first step we need one RHEL based host(VM/PM), running a subscribed installation of Red Hat Enterprise Linux (RHEL) 8.6 and enable below repo's to install the rpm's.

_Red Hat Enterprise Linux 8 for x86_64 - AppStream_

_Red Hat Enterprise Linux 8 for x86_64 - BaseOS_

_Red Hat OpenShift Container Platform 4.12 for RHEL 8 x86_64_

_Red Hat Ansible Engine 2.9 for RHEL 8 x86_64_

```bash
  STEP 1:- Dependencies to be installed on bastion host.
  
  # dnf -y install ansible python3-netaddr skopeo podman openshift-clients ipmitool python3-pyghmi python3-jmespath git
```
```bash
  STEP 2:- Download crucible playbooks.
  
  # git clone https://github.com/redhat-partner-solutions/crucible.git
```
**Before moving to next step please confirm below mentioned points.**

* inentory.yml & inventory.vault.yml file under crucible folder should be updated with right data/information.
* pull-secrect.txt should be present inside the crucible folder.
* Cilium CNI manifest are present in crucible folder and image path are updated according to your ENV you can download these manifest from cilium.io according to your required version.

```bash
  STEP 3:- Run below playbook.
  
  
  # ansible-playbook -i inventory.yml site.yml -e "@inventory.vault.yml" 
```
**You can check your cluster installation status/progress form Assisted installer GUI from bastion host. you can open it by using "http://localhost:8080".**
## Documentation

[Redhat Crucible ](https://github.com/redhat-partner-solutions/crucible)

[Cilum CNI](https://docs.cilium.io/en/stable/)


## Authors

- [@shashank-github](https://github.com/shashank-6777)
- [@shashank-linkedin](https://linkedin.com/in/shashank-sharma-137002124)

