AWS Zookeeper Cluster
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

    - hosts: localhost
    connection: local
    gather_facts: true
    user: root
    become: yes
    become_user: root
    vars:
      # DNS
      route_53_internal: true
      route_53_external: false
      int_dns_zone: local.
      int_dns_record: zookeeper-1
      int_dns_vpc:
      int_dns_type: A
      int_dns_ttl: 60
      domain_name: "{{ int_dns_record }}.{{ int_dns_zone }}"
      # Supervisor (Only set this to true if you are using the Amazon Linux AMI)
      supervisor:
        amazon_ami: true
      # Zookeeper
      # Exhibitor
      exhibitor:
        configtype: s3
        s3_bucket: com.eu-west-1.zookeeper
    roles:
      - dns
      - supervisor
      - zookeeper
      - exhibitor
    post_tasks:
      - name: Reread supervisor
        command: /usr/local/bin/supervisorctl reread
      - name: Update supervisor
        command: /usr/local/bin/supervisorctl update
      - name: Restart service
        command: /usr/local/bin/supervisorctl restart exhibitor
      - name: Restart server
        command: sudo reboot now

*Please note, we have included the example above as a file named: zookeeper_node.yml*