# OCPLabs

## Creer un projet nomme: intranet
```
 oc new-project intranet
```

## Creer un deploiement MySQL avec les carateristiques suivantes:
Nom: intranet-db
Image: quay.io/fedora/mysql-80

```
oc create deployment intranet-db --image=quay.io/fedora/mysql-80
```

Variables d'environnement:
 MYSQL_ROOT_PASSWORD=rootpass
 MYSQL_USER=loic
 MYSQL_PASSWORD=pass
 MYSQL_DATABASE=wpdb

```
oc set env deployment/intranet-db MYSQL_ROOT_PASSWORD=rootpass MYSQL_USER=loic MYSQL_PASSWORD=pass MYSQL_DATABASE=wpdb
```

Creer un service pour exposer le deploiement MySQL sur le port 3306

```
oc expose deployment intranet-db --port 3306
```


## Creer un deploiement WordPress avec les carateristiques suivantes:
Nom: wordpress
Code Source: quay.io/fedora/mysql-80

```
oc new-app https://github.com/WordPress/WordPress.git
```
