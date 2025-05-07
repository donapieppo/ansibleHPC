# unibo.hpc.ssh_limit_access role

Aggiunge

```
AllowGroups {{ " ".join(sshd_allowed_groups) }}
```

al file `/etc/ssh/sshd_config.d/99_permit_only_adm_group.conf`
in modo da limitare accesso agli utenti elencati nella variabile
sshd_allowed_groups.

Da usare nei nodi di calcolo.
