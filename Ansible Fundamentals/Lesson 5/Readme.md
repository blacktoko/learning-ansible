Continue on the environment that you've created in the Lesson 4 Lab. Modify the environment in such a way that SSL configuration is pushed to the server that is a member of the LAMP group used in Lesson 4. Consider the following requirements:

- To provision this environment, use the control.ansible.local host as a web server that provides some files. In the web server document root on this server, create a file with the name https.conf and transfer it to the /etc/httpd/conf.d/ directory of the managed machines. I will show sample content for this file shortly. Also provide SSL keys. You can easily generate these keys using the **genkey** utility on the control host. Run **genkey managed2.ansible.local** and follow all default prompts to create the keys, after which you can put them in the Apache document root on the control host as well. Compress these files in a tar file and provide the tar file
- Use the appropriate Ansible module to extract the tar file
- Create the https.conf file from the previous step as a template. Use facts so that it can dynamically determine the host name of the target host.
- Ensure that the SSL configuration is only deployed on machines that have at least 512 MiB of RAM
- Use a master playbook.yml file from which includes are done to a few secondary files
  - The packages.yml file uses loop iteration to install a list of items tat are provided. These items must be the wep package httpd and the ssl package mod_ssl. Provide these items through variables, which makes it easier to use between different Linux distributions
  - Create an include file that fetches the files from http://control.ansible.local and puts them in the appropriate directories. Here also, use variables to refer to these directories as it makes it easier to meet with differences between Linux distributions.
  - Also create a firewall configuration file that is included and opens the firewalld firewall for the services that have been enabled.

### Sample https.conf file
```
Listen 192.168.4.35:443
NameVirtualHost managed2.ansible.local

<VirtualHost managed2.ansible.local:443>
  ServerName managed2.ansible.local
  DocumentRoot /var/www/html
  SSLEngine on
  SSLCertificateFile /etc/httpd/conf.d/ssl/server.crt
  SSLCertificateKeyFile /etc/httpd/conf.d/ssl/server.key
</VirtualHost>
