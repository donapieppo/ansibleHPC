# Unibo HPC

Collezione di ansible rules per configurare nodi nel cluster Navile.

## Utilizzo

Esempio:

```bash
mkdir ansible-chimica
cd ansible-chimica

cat > requirements.yml <<EOF
collections:
  - name: git@github.com:donapieppo/ansibleHPC.git
    type: git
    version: main
EOF

ansible-galaxy collection install -r requirements.yml
```

## Esempio di inventory (`inventory.yaml`)

```yaml
all:
  children:
    chimica_hosts:
      hosts:
        lnvp-node-03.hpc.unibo.it:
```

## Esempio di playbook (`chimica.yaml`)

```yaml
---
- name: HPC chimica
  hosts: chimica_hosts
  become: true
  roles:
    - common
    - ldap_client
    - nss_ldap
    - munge
    - slurmd
    - lmod
    - node_software
    - ssh_limit_access
    - chrony
    - ceph_client
```

