# ACIT 2420 Final Exam

*Aaron Zhang*

*A01316218*

## Part 1

```
sudo apt update
sudo apt upgrade
```

## Part 2

> :%s/V/C/g

> :%s/eco/echo/g

> :%s/numbs/:digit:/g

![p2](Images/p2.png)

## Part 3

`man journalctl -K "boot"`
![p3](Images/p3_boot.png)

`man journalctl -K "priority"`
![p3](Images/p3_prio.png)

`man journalctl -K "json"`
![p3](Images/p3_o.png)
![p3](Images/p3_json.png)

**Working command:**
![p3](Images/p3_command.png)


## Part 4

**find_users script version 1:**
```bash
#!/bin/bash

printf "Regular users on the system are:\n"
grep ':[1-5][0-9][0-9][0-9]:' /etc/passwd | awk -F: '{print $1 " " $3 " " $7}'

printf "\nUsers currently logged in are:\n"
users
```

**Output of find_users v1:**
![p4](Images/p4_output.png)



## Part 5

`sudo vim /etc/systemd/system/p5.service`
```ini
[Unit]
Description=Run script from part 4

[Service]
ExecStart=/bin/bash /home/vagrant/find_users

[Install]
WantedBy=multi-user.target
```

**Status of p5.service:**
![p5](Images/p5_status.png)

*Note: p5.service is located in /etc/systemd/system*

## Part 6

`sudo vim /etc/systemd/system/p5.timer`

```ini
[Unit]
Description=Timer for p5.service

[Timer]
OnBootSec=1min
OnUnitActiveSec=1d
Unit=p5.service
Persistent=true

[Install]
WantedBy=timers.target
```

**Start, enable, status for p5.timer:**
![p6](Images/p6_status.png)

**Status of p5.service:**
![p6](Images/p6_service_status.png)