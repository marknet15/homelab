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

## Examples

`portainer.yml`

```yaml
---
namespace: tools
create_record: true
chart:
  name: portainer
  path: portainer/portainer
  repo:
    name: portainer
    url: https://portainer.github.io/k8s/
chart_values:
  image:
    repository: portainer/portainer-ce
    tag: 2.14.2
    pullPolicy: Always
  serviceAccount:
    annotations: {}
    name: portainer-sa-clusteradmin
  ingress:
    enabled: true
    ingressClassName: ""
    annotations:
      kubernetes.io/ingress.class: traefik
    hosts:
      - host: portainer.marknet15.com
        paths:
          - path: "/"
    tls: []
```
