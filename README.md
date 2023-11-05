# Simple Network Scanner

## The Simple Network Scanner Web App (nmap) is a project that allows you to create a network scanner accessible from a web browser on the network.
1. *Prerequisites*: Linux – Cron Jobs for Scheduled Tasks (crontab), Linux – Change Permissions and Ownership for Files and Folders (chmod, chown, members, groups)
2. *Install Apache2, PHP, and nmap*: Use the command `sudo apt-get install apache2`, `sudo apt-get install php`, and `sudo apt-get install nmap`.
3. *Configure Ownership and Permissions*: Use the command `sudo chown ubuntu /var/www/html` and `sudo chmod 777 /var/www/html`.
4. *Cron Job Configuration*: Use the command `sudo crontab -e` and add the line `/10 * * * * nmap 192.168.1.0/24 -oN /var/www/html/nmap.html` to the crontab file.
5. *Create a PHP file (network.php)*: The code is presented in `network.php`

### Steps to follow:
1. *To Check for Live Hosts*- `sudo nmap -sn 192.168.52.0/24 -oN live_hosts.txt`
2. *For OS Detection* -
  
- command to create a new file called ip-addresses.txt that will include only the live IP addresses.`grep "Nmap scan report for" live_hosts.txt | awk '{print $5}' > ip-addresses.txt`
- run the Nmap OS detection scan - `sudo nmap -iL ip-addresses.txt -O -oN os_detection.txt`


3. *For Service Scan* - `nmap -iL ip-addresses.txt -sV -oN common_services.txt`
4. *For Vulnerability scan* - `nmap -iL ip-addresses.txt -script vuln -oN vulnerabilities.txt`


### Install Apache2, PHP and nmap

`sudo apt-get install apache2`

`sudo apt-get install php` 

`sudo apt-get install nmap`

###  Ownership and Permissions

`sudo chown ubuntu`

`sudo chmod 777 html`

### Configure Ownership and Permissions

`sudo chown ubuntu /var/www/html`

`sudo chmod 777 /var/www/html`

### Cron Job Configuration

`sudo crontab -e`

`*/10 * * * * nmap 192.168.1.0/24 -oN /var/www/html/nmap.html`

### network.php

<?php

echo "Server Timestamp: ";
echo date("h:i:sa");

echo "<pre>";
include("nmap.html");
echo "</pre>";

?>
