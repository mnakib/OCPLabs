# OCPLabs

## Create a project named _intranet_

The _intranet_ project will contain your WordPress application

<details>
  <summary>Check Solution</summary>
  ```bash
  oc new-project intranet
  ```
</details>
  
## Creer un deploiement MySQL avec les carateristiques suivantes:
- _Nom: intranet-db_
- _Image: quay.io/fedora/mysql-80_

```
oc create deployment intranet-db --image=quay.io/fedora/mysql-80
```

### Injecter les variables d'environnement suivantes dans le deploiement _intranet-db_

- _MYSQL_ROOT_PASSWORD=rootpass_
- _MYSQL_USER=user_
- _MYSQL_PASSWORD=pass_
- _MYSQL_DATABASE=wpdb_

```
oc set env deployment/intranet-db MYSQL_ROOT_PASSWORD=rootpass MYSQL_USER=user MYSQL_PASSWORD=pass MYSQL_DATABASE=wpdb
```

### Creer un service pour exposer le deploiement MySQL sur le port 3306

```
oc expose deployment intranet-db --port 3306
```


## Creer un deploiement WordPress avec les carateristiques suivantes:
- _Nom: wordpress_
- _Code Source: https://github.com/WordPress/WordPress.git_

```
oc new-app https://github.com/WordPress/WordPress.git
```

### Creer une route qui exposera le service _wordpress_

```
oc expose service wordpress
```
