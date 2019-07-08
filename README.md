## kubernetes - mStakx-test (Level 1)

# Introduction:

This repo contains code and scripts to demonstrate kubernetes cluster installation on GCE not using GKE, followed by multiple tasks as required in mStakx kubernetes test (level1). 


# Environment description:

- Localhost CentOS 7.6
- Ansible v 2.8.1
- Python v 2.7.5
- GCP Account
- gcloud installed
- kubectl installed


# Before you start:

1- Make sure that gcloud is set to use the Google Cloud Platform project you want

   `$ gcloud config set project <project-id>`

2- Make sure you have credentials for GCloud by running 

   `$ gcloud auth login`


# Cloning Steps:

1- Clone the git repo k-ghazaly/kubernetes

   `$ git clone https://github.com/k-ghazaly/kubernetes.git`

2- Running Ansible playbook kubernetes.yml
   This playbook should run through all the test requirements, and it is designed to be idempotent.

   `$ ansible-playbook kubernetes.yml`

3- For testing the horizontal pod autoscaler deployed in staging namespace, run the load-test bash script provided in new terminal, and in another terminal watch how the hpa functions

 - Terminal1: `$ ./load-test.sh`
 - Terminal2: `$ watch kubectl -n staging get hpa`

  Within a minute or so, we should see the higher CPU load by executing.

  To stop the load, from terminal1 terminate the load generation by typing <Ctrl> + C.


# Notes:

1- As per the minimum recommendations for kubernetes cluster resource, I've chosen the below instances types:
 - Master : n1-standard-1
 - Workers: n1-standard-2

2- For cluster monitoring I would deploy Prometheus, configure alerts with Alertmanager and dashboards with Grafana. As during my technical work experience it has been proved that this stack is the most powerfull and stable monitoring tool for Kubernetes and OpenShift. 
   In addtition to:
   - The model is based on key-value pairs, similar to how Kubernetes itself organizes infrastructure metadata using labels. It allows for flexible and accurate time series data, powering its Prometheus query language.
   - Exposing prometheus metrics is a pretty straightforward task. Metrics are human readable, are in a self-explanatory format, and are published using a standard HTTP transport. 

3- To destroy the kubernetes cluster and all assotiate resources 
   $ kubernetes/cluster/kube-down.sh


# References:

- Kubernetes deployment: https://kubernetes.io/docs/setup/production-environment/turnkey/gce/
- Ingress Controller:    https://github.com/nginxinc/kubernetes-ingress/blob/master/docs/installation.md
- Guest Book App:        https://kubernetes.io/docs/tutorials/stateless-application/guestbook/

