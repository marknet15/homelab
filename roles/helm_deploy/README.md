# Ansible role to deploy Helm charts

Ansible role to configure a chart repo and deploy the chart to Kubernetes.

## Useage

Example playbook:

```yaml
---
- hosts: k3s
  gather_facts: false
  vars_prompt:
    - name: deployment_name
      prompt: "Please specify the deployment name"
      private: false
  tasks:
    - name: Include deployment vars
      ansible.builtin.include_vars:
        file: "deployments/k8s/{{ deployment_name }}.yml"

    - name: Deploy helm chart
      ansible.builtin.include_role:
        name: marknet15.homelab.helm_deploy
```
