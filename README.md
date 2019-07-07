# kubernetes - mStakx-test (Level 1)

Introduction:
This repo contains code,scripts and documents demonistrates kubernetes cluster installation on GCE not using GKE, follwed by multiple tasks as requered in mStakx kubernetes test (level1). 

Author:
Kareem Ghazaly

Prerequisites:
- Ansible v 2.8
- Python v 2.7
- gcloud 
- GCP Account
- kubectl

Before you start:
1- Make sure that gcloud is set to use the Google Cloud Platform project you want
   gcloud config set project <project-id>

2- Make sure you have credentials for GCloud by running gcloud auth login.

Clonning Steps:

1- Clone the git repo k-ghazaly/kubernetes
   # git clone https://github.com/k-ghazaly/kubernetes.git

2- Running Ansible playbook kubernetes.yml
   This playbook should run through all the test requirements, and it is designed to be idiomatic.
   # ansible kubernetes.yml

Notes:

1- After deploying the guestbook application in both namespaces staging and production, you have to add two records in /etc/hosts file to resolve the required hostnames
   Ex:
       104.197.43.162 staging-guestbook.mstakx.io
       104.197.43.182 guestbook.mstakx.io

