# My lab setup of dvwa docker container in ubuntu lab

---

## Prerequisites
- Set up an ubuntu lab
- Put static IP address in ubuntu lab
- Update machine
- Pull dvwa docker image

---

### 1. Pull docker Image 

```bash
userver@userver:~$ docker images
REPOSITORY               TAG       IMAGE ID       CREATED         SIZE
nginx                    latest    60adc2e137e7   2 days ago      152MB
alpinelinux/docker-cli   latest    e8b7b76791d8   12 months ago   163MB
sagikazarmark/dvwa       latest    e901498e651a   8 years ago     359MB
```

### 2. Run docker image, bind port 80 of docker to port 8080 of host machine

```bash
userver@userver:~$ docker run -d --name dvwa -p 8080:80 sagikazarmark/dvwa 
0994c13ddeb9893a544bbe3c300943fdf2281f375321001832b3ef903fdc0fd1

userver@userver:~$ docker ps -a
CONTAINER ID   IMAGE                COMMAND     CREATED          STATUS          PORTS                                               NAMES
0994c13ddeb9   sagikazarmark/dvwa   "/run.sh"   35 seconds ago   Up 33 seconds   3306/tcp, 0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   dvwa
```

- Dvwa accessable on http://ubuntu-server-ip:8080/ which is http://192.168.0.50:8080/login.php


[Dvwa setup](1.png)


### 3. Stop the docker image

```bash
userver@userver:~$ 
userver@userver:~$ docker stop dvwa 
dvwa
```

### 4. Read Dvwa server logs

```bash
userver@userver:~$ docker logs dvwa

Starting MySQL database server: mysqld . ..
Checking for tables which need an upgrade, are corrupt or were 
not closed cleanly..
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
Starting web server: apache2.
tail: unrecognized file system type 0x794c7630 for '/var/log/apache2/access.log'. please report this to bug-coreutils@gnu.org. reverting to polling

==> /var/log/apache2/access.log <==
192.168.0.102 - - [20/Nov/2025:17:39:40 +0000] "GET / HTTP/1.1" 302 533 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:39:41 +0000] "GET /login.php HTTP/1.1" 200 1048 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:39:41 +0000] "GET /dvwa/css/login.css HTTP/1.1" 200 741 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:39:41 +0000] "GET /dvwa/images/login_logo.png HTTP/1.1" 200 9374 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:39:41 +0000] "GET /favicon.ico HTTP/1.1" 200 1706 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:43:01 +0000] "POST /login.php HTTP/1.1" 302 364 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:43:01 +0000] "GET /setup.php HTTP/1.1" 200 1872 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:43:01 +0000] "GET /dvwa/css/main.css HTTP/1.1" 200 1445 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:43:01 +0000] "GET /dvwa/js/dvwaPage.js HTTP/1.1" 200 763 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:43:01 +0000] "GET /dvwa/images/logo.png HTTP/1.1" 200 5330 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:43:01 +0000] "GET /dvwa/images/spanner.png HTTP/1.1" 200 748 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:44:49 +0000] "POST /setup.php HTTP/1.1" 302 365 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:44:50 +0000] "GET /setup.php HTTP/1.1" 200 1978 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:44:56 +0000] "GET /login.php HTTP/1.1" 200 1050 "http://192.168.0.50:8080/setup.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:04 +0000] "POST /login.php HTTP/1.1" 302 364 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:04 +0000] "GET /login.php HTTP/1.1" 200 1065 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:17 +0000] "POST /login.php HTTP/1.1" 302 364 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:17 +0000] "GET /index.php HTTP/1.1" 200 3041 "http://192.168.0.50:8080/login.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:31 +0000] "GET /security.php HTTP/1.1" 200 2461 "http://192.168.0.50:8080/index.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:31 +0000] "GET /dvwa/images/lock.png HTTP/1.1" 200 1045 "http://192.168.0.50:8080/security.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:34 +0000] "POST /security.php HTTP/1.1" 302 451 "http://192.168.0.50:8080/security.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:34 +0000] "GET /security.php HTTP/1.1" 200 2475 "http://192.168.0.50:8080/security.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:38 +0000] "GET / HTTP/1.1" 200 3013 "http://192.168.0.50:8080/security.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:45:41 +0000] "GET /instructions.php HTTP/1.1" 200 4873 "http://192.168.0.50:8080/" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"
192.168.0.102 - - [20/Nov/2025:17:48:18 +0000] "GET / HTTP/1.1" 200 3014 "http://192.168.0.50:8080/instructions.php" "Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0"

userver@userver:~$ 
```
- My machine [192.168.0.102] accesses and interacts with the server
- User agent: Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0



