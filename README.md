# Deploy ldap server with phpldapadmin UI to Kubernetes

`kinflate inflate -f . | kubectl apply -f -`

## Check that ldap server and phpldapadmin have started successfully

`kubectl get service`

Should show two service names:

```
ldap-service
phpldapadmin-service
```

Next open phpldapadmin UI by https://<external_ip>:443, where the external_ip can be get by

`kubectl get service -o yaml | grep "ip"`

Now login by

```
Login DN: cn=admin,dc=example,dc=org
Password: admin
```

Apply a search by clicking the search button on the left. You will see two entries.


Add a new entry by importing. Click the import button on the left and paste following content in the prompt box and proceed.

```
dn: cn=The Postmaster,dc=example,dc=org
objectClass: organizationalRole
cn: The Postmaster
```

This adds a new entry for _The Postmaster_. Click the refresh button on the left. You will see the directory has three entries.