# spring-config-server-demo
Just a demo application on how to configure a Spring config server. 

### Initial setup
##### 1. Setup a local git inside a directory 
Store the necessary properties in a yml or properties file and commit the changes

##### 2. Link git server
Goto application.yml and update below property:
```sh
spring.cloud.config.server.git.uri: <path to your git directory>
```

##### 3. Setup secret key
If planning to store encrypted values in config then set a secret key inside ```bootstrap.properties```:
```sh
encrypt.key=yoursecretkey
```

### Operations
##### View config properties
To view config for a particular environment make this GET call:
```http://localhost:8888/<app-name>/<env>```
eg: ```http://localhost:8888/orders/local```

##### Encrypt a property
To get encrypted value of a property, just make below POST call:
```
curl --location --request POST 'http://localhost:8888/encrypt' \
--header 'Content-Type: application/json' \
--data-raw 'Property Value To Be Encrypted'
```
