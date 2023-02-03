# Serving Files outside of htdocs with xampp and Apache
Simple steps to serve files outside of htdocs folder in xaamp/apache 

1. Virtual Host
  a. Open C:\xampp\apache\conf\extra\httpd-vhosts.conf
  b. Un-comment ~line 19 (NameVirtualHost *:80).
  c. Add your virtual host
    ```
    <VirtualHost *:80>
        DocumentRoot D:\projects\mypro
        ServerName mypro.local
        <Directory D:\projects\mypro>
            Order allow,deny
            Allow from all
        </Directory>
    </VirtualHost>
    ```

1. Open your hosts file and add the following (C:\Windows\System32\drivers\etc\hosts)

```
127.0.0.1 mypro.local 
```

3. Open http.conf and change the following. 
```
    DocumentRoot "C:/xampp/htdocs"
    <Directory "C:/xampp/htdocs">
```
to 
```
    DocumentRoot "D:/projects"
    <Directory "D:/projects">
```

1. In the ```<IfModule alias_module></IfModule>```
 block, include the Alias mapping as below. 
```
   Alias /mypro "D:/projects/mypro"

```