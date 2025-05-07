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
    - unibo.hpc.common
    - unibo.hpc.ldap_client
    - unibo.hpc.nss_ldap
    - unibo.hpc.munge
    - unibo.hpc.slurmd
    - unibo.hpc.lmod
    - unibo.hpc.node_software
    - unibo.hpc.ssh_limit_access
    - unibo.hpc.chrony
    - unibo.hpc.ceph_client
```

