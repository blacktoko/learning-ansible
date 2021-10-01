# Lesson 3 Lab2: Preparing OpenStack Hosts

This lab comes from my own practice. I'm using it to prepare OpenStack hosts. Even if you're not using Openstack, you can run this lab as well.

1. For a test, run this lab on one random node:
  - Disable the NetworkManager service
  - Modify the /etc/default/grub file and add the parameters net.ifnames=0 and biosdevname=0 to the line that loads the Linux kernel. Next copy the new file to all managed hosts
  - On all hosts run grub2-mkconfig to write the modified /etc/default/grub file
2. Tip! Use the lineinfile module to edit the configuration file