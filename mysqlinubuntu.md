## Mysql Installation
### Version 8.0.36
`sudo -i`
```
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation
```
>verify that MySQL is running by typing:
```
sudo systemctl status mysql
```
>Log in to the MySQL server as the root user. Since there's no password set, you can use the following command:
```
sudo mysql
```
>Once you're logged in to the MySQL shell, you can set the root password using the following command. Replace new_password with your desired password:
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'new_password';
```
```
FLUSH PRIVILEGES;
```
`exit; `

> check the port running of mysql
```
sudo ss -tuln | grep 3306
```
> Restart mysql services
```
sudo systemctl restart mysql
```
> login with root user with password
```
mysql -u root -p
```
> First, create the user with the password:
```
CREATE USER 'username'@'22.22.22.22' IDENTIFIED BY 'password';
```
> Grant previlige to the users
```
GRANT ALL PRIVILEGES ON *.* TO 'username'@'22.22.22.22' WITH GRANT OPTION;
```
`FLUSH PRIVILEGES;`

> GCP Note: Create a firewall to allow TCP network traffic to mysql instance on port 3306
> Check public ip is enabled
## Check MySQL Bind Address:
goto root user `sudo -i`
```
/etc/mysql/mysql.conf.d/mysqld.cnf
```
>Ensure that the bind-address parameter is set to either 0.0.0.0 (to listen on all interfaces) or the specific IP address of the VM. If it's set to 127.0.0.1, MySQL will only listen for connections on the localhost interface.
