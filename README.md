# OCPLabs

## Create a project named _intranet_

The _intranet_ project will contain your WordPress application

<details>
  <summary>Check Solution</summary>
  
  ```
  oc new-project intranet
  ```

</details>
  
## Creer un deploiement MySQL avec les carateristiques suivantes:
- _Nom: intranet-db_
- _Image: quay.io/fedora/mysql-80_

<details>
  <summary>Check Solution</summary>
  
  ```
  oc create deployment intranet-db --image=quay.io/fedora/mysql-80
  ```
  
</details>




### Injecter les variables d'environnement suivantes dans le deploiement _intranet-db_

- _MYSQL_ROOT_PASSWORD=rootpass_
- _MYSQL_USER=user_
- _MYSQL_PASSWORD=pass_
- _MYSQL_DATABASE=wpdb_

<details>
  <summary>Check Solution</summary>
  
  ```
  oc set env deployment/intranet-db MYSQL_ROOT_PASSWORD=rootpass MYSQL_USER=user MYSQL_PASSWORD=pass MYSQL_DATABASE=wpdb
  ```

</details>

### Creer un service pour exposer le deploiement MySQL sur le port 3306

<details>
  <summary>Check Solution</summary>
  
  ```
  oc expose deployment intranet-db --port 3306
  ```
</details>


## Creer un deploiement WordPress avec les carateristiques suivantes:
- _Nom: wordpress_
- _Code Source: https://github.com/WordPress/WordPress.git_

<details>
  <summary>Check Solution</summary>
  
  ```
  oc new-app https://github.com/WordPress/WordPress.git
  ```
</details>

### Creer une route qui exposera le service _wordpress_

```
oc expose service wordpress
```
