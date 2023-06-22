# Overview
An Ansible playbook that installs Kubernetes.

A guide for using this repo to spin up a Kubernetes cluster is available at [Installing your Kubernetes homelab cluster in minutes with Ansible](https://perdue.dev/installing-your-kubernetes-homelab-cluster-in-minutes-with-ansible/)

# ips
- ansible 192.168.1.22
- master  192.168.1.21
- node01  192.168.1.23


# Features
- containerd
- calico for pod networking

# Important
- ubuntu ' to access as a root ' , (Apply on Master and Worker Nodes )
    - vim /etc/ssh/sshd-config

        - 1) FROM: #PermitRootLogin prohibit-password ==> TO: PermitRootLogin yes

        - 2) sudo systemctl restart ssh

        - 3) sudo passwd " change password "

- (Apply on Ansible )
    - ssh-keygen
    - ssh-copy-id root@ip-master
    - ssh-copy-id root@ip-worker

- (Apply on Master )
    - ssh-keygen
    - ssh-copy-id root@ip-worker


# Quickstart
```
ansible -i inventory/dev all -m ping

ansible-playbook -i inventory/dev playbooks/k8s_all.yaml

# reboot might be required after installation
ansible -i inventory/dev all -a "/sbin/reboot" --become
```
