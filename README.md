# Simple Network Scanner

The Simple Network Scanner Web App (nmap) is a project that allows you to create a network scanner accessible from a web browser on the network.
1. *Prerequisites*: Linux – Cron Jobs for Scheduled Tasks (crontab), Linux – Change Permissions and Ownership for Files and Folders (chmod, chown, members, groups)
2. *Install Apache2, PHP, and nmap*: Use the command `sudo apt-get install apache2`, `sudo apt-get install php`, and `sudo apt-get install nmap`.
3. *Configure Ownership and Permissions*: Use the command `sudo chown ubuntu /var/www/html` and `sudo chmod 777 /var/www/html`.
4. *Cron Job Configuration*: Use the command `sudo crontab -e` and add the line `/10 * * * * nmap 192.168.1.0/24 -oN /var/www/html/nmap.html` to the crontab file.
5. *Create a PHP file (network.php)*: The code is presented in `intel.php`


- A Cron Job is used every 10 minutes to trigger nmap to scan the network and output the results into a text file.
- A PHP file is used to format the text file, add a few things, and present the results for a web browser.
