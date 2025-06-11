# Sprawozdanie Patryk Miścisz

## 1. Uruchomienie LEMP-a

```bash
docker-compose -p lab12 up -d
```
### Wynik:
```bash
[+] Running 51/51
 ✔ mysql Pulled                                                                                         21.6s 
 ✔ php Pulled                                                                                           19.5s 
 ✔ phpmyadmin Pulled                                                                                    21.0s 
 ✔ nginx Pulled                                                                                         13.6s 
[+] Running 7/7
 ✔ Network lab12_backend      Created                                                                    0.1s 
 ✔ Network lab12_frontend     Created                                                                    0.0s 
 ✔ Volume "lab12_db_data"     Created                                                                    0.0s 
 ✔ Container lemp-mysql       Started                                                                    1.2s 
 ✔ Container lemp-php         Started                                                                    1.2s 
 ✔ Container lemp-nginx       Started                                                                    1.0s 
 ✔ Container lemp-phpmyadmin  Started                                                                    0.9s
```
## 2. Sprawdzenie działania kontenerów:
```bash
docker ps
```
### Wynik:
```bash
CONTAINER ID   IMAGE                       COMMAND                  CREATED         STATUS         PORTS                  NAMES
e6e89789f07c   nginx:1.25                  "/docker-entrypoint.…"   4 minutes ago   Up 4 minutes   0.0.0.0:4001->80/tcp   lemp-nginx
b2cf8f66ba54   phpmyadmin/phpmyadmin:5.2   "/docker-entrypoint.…"   4 minutes ago   Up 4 minutes   0.0.0.0:6001->80/tcp   lemp-phpmyadmin
9b372707ca47   php:8.2-fpm                 "docker-php-entrypoi…"   4 minutes ago   Up 4 minutes   9000/tcp               lemp-php
0dc7c7f13dae   mysql:8.3                   "docker-entrypoint.s…"   4 minutes ago   Up 4 minutes   3306/tcp, 33060/tcp    lemp-mysql
```
## 3. Strona logowania phpMyAdmin(http://localhost:6001/):
![logowanie phpMyAdmin](/screenshots/stornalogowania.png)

## 4. Strona po zalogowaniu do phpMyAdmin(http://localhost:6001/):
### Dane logowania zawarte w docker-compose.yml:
```bash
MYSQL_USER: testuser
MYSQL_PASSWORD: testpassword
```
![widok po zalogowaniu](/screenshots/widok%20po%20zalogowaniu.png)

### 5. Testowa baza danych dodana w docker-compose.yml:
```bash
MYSQL_DATABASE: testdb
```
![testowa baza danych](/screenshots/bazaTestowa.png)

### 6. Strona index.php (http://localhost:4001):
```bash
<?php
phpinfo();
?>
```
![strona index.php](/screenshots/indexphp.png)