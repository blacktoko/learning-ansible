# Lesson 3 Lab1: Working with ansible playbooks

Create a playbook that will install httpd on the managed server, using the following requirements:
 - Install the httpd package
 - Enable the httpd service and make sure it is started
 - Create the file /var/www/html/index.html, containing the text "Welcome to my web server"
 - Use the firewalld module to open the appropiate ports in the firewall