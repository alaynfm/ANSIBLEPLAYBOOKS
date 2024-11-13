# Intall AWX on eks

## Prerequisites
- A working eks with permissions to create resources as lb
- Node group - minimum 2 nodes (t3.xlarge)
- kubectl installed with the eks context configured

# Installation

```bash
#download awx-operator from official repo
git clone https://github.com/ansible/awx-operator.git
cd awx-operator
git tag 0.20.0


#create the configurations files
vi kustomization.yaml
vi persistent.yaml
vi awx-clb-without-tls.yaml

#apply changes
kubectl create -k .

kubectl edit pvc ***** -n aws

# add/change the following
spec:
...
  storageClassName: manual

#view results
watch kubectl get pods -n awx
```
