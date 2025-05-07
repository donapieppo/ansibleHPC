# unibo.hpc.ssh_keys_from_ldap role

Installa lo script `/usr/local/sbin/ldap_authorized_keys` che
via `ldapsearch` ritorna il valore di `sshPublicKey` per l'utente.

Quindi configura via `/etc/ssh/sshd_config.d/99_ldap_authorized_keys.conf`


```
AuthorizedKeysCommand /usr/local/sbin/ldap_authorized_keys
AuthorizedKeysCommandUser nobody
```

in modo da far accedere gli utenti via la chiave pubblica
in ldap.

