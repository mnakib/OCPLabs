# OCPLabs

## Create a project named _intranet_

The _intranet_ project will contain your WordPress application

<details>
  <summary>Check Solution</summary>
  
  ```
  oc new-project intranet
  ```

</details>
  
## Create a MySQL MySQL with below specifications:
- _Nom: intranet-db_
- _Image: quay.io/fedora/mysql-80_

<details>
  <summary>Check Solution</summary>
  
  ```
  oc create deployment intranet-db --image=quay.io/fedora/mysql-80
  ```
  
</details>


### Inject below environment variables to the _intranet-db_ MySQL deployment

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

### Create a service to expose the _intranet-db_ MySQL deployment on port 3306

<details>
  <summary>Check Solution</summary>
  
  ```
  oc expose deployment intranet-db --port 3306
  ```
</details>


## Create a WordPress deployment with below specifications:
- _Nom: wordpress_
- _Code Source: https://github.com/WordPress/WordPress.git_

<details>
  <summary>Check Solution</summary>
  
  ```
  oc new-app https://github.com/WordPress/WordPress.git
  ```
</details>

By using the ```oc new-app``` command, OCP will create a deployment along with a service needed to communicate with it.

### Create a route to expose the _wordpress_ service

```
oc expose service wordpress
```
