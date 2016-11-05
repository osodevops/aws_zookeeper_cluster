#AWS Zookeeper Cluster
------------

This is an Ansible playbook and also guide on how to setup Zookeeper on AWS in a clustered mode.

Requirements
------------
* Ansible v2.1
* Boto
* AWS IAM Profile with S3 Access
* AWS AutoScalingGroups
* AWS Route53 internal DNS

This playbook assumes you have setup your AWS account and installed the latest version of Ansible and Boto.

Guide
--------------

### UPDATES COMING SOON!

Playbook/Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
