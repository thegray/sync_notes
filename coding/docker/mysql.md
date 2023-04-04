## Run Mysql container with Custom port
### Unix
```docker run --detach --name={container_name} -p {port_to_use}:3306 --env="MYSQL_ROOT_PASSWORD={mysql_password}" mysql```

### How To Connect
#### Terminal
```mysql -h 127.0.0.1 -P {port_to_use} -u root -p```

