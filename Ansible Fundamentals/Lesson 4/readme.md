# Lesson 4 Lab: Working with Variables, Inclusions, and Task Conrol

1. Create an Ansible configuration that sets up hosts Ansible1 and Anible2 for automatic installation. Create custom facts for both hosts and use variable inclusion to realize this. To configure ansible1, use a host group with the name "file", to configure ansible2, use a host group with the name "lamp"
2. Create a file with the name custom.fact that defines the custom facts. In this file, define two sections. The section "package" contains the following:
  - smb_package = smb
  - ftp_package = ftp
  - db_package = mariadb
  - web_package = http
The section service contains service variables for the packages mentioned above. Use the name smb_service etc. and set the variable to the appropiate name of the service.
3. Create a playbook with the name copy_facts.yml that copies these facts to all managed hosts. Define a variable with the name "remote_dir" and a variable with the name "fact_file" and use these. Use the file and copy modules.
4. Run the playbook and verify it worked.
5. Create a variable inclusion file with the name ./vars/allvars.yml and set the following variables
  - web_root: /var/www/html
  - ftp_root: /var/ftp
6. create a tasks directory in the project folder. In this directory, create two YAML files, one that installs, starts and enables the LAMP services; and one that installs, starts, and enables the file services
7. Create the main playbook that will set up the lamp services and the file servers with the packages they need, using inclusions to the previously-defined tasks file. Also, ensure that it opens the firewalld to allow access to these servers. Finaly, the web services should be provided with an index.hmtl file that shows "managed by Ansible" on the first line
8. Run the playbook
9. Use ad hoc commands to verify the services have been started
