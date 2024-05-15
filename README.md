`dimmaryanto93.opensearch`
=========

Repository ini digunakan untuk menginstall [Apache Skywalking]() yaitu berfungsi Application Performance Monitoring atau APM untuk Linux

Support platform

- CentOS
- Oracle Linux 
- RedHat


Ansible - User Guide
------------

1. Authenticate with private-key for login ssh, generate ssh key on your local machine then use `ssh-copy-id user@your-ip-server` to copy public key to your server.


Requirements
------------

Untuk menggunakan role ini, kita membutuhkan package/collection 

- [ansible.posix](https://github.com/ansible-collections/ansible.posix)
- [community.general](https://github.com/ansible-collections/community.general)

Temen-temen bisa install, dengan cara 

```bash
ansible-galaxy collection install ansible.posix community.general
```

Atau temen-temen bisa menggunakan `requirement.yaml` file and install menggunakan `ansible-galaxy collection install -r requirement.yaml`, dengan format seperti berikut:

```yaml
---
collections:
  - community.general
  - ansible.posix
```

Role Variables
--------------

Ada beberapa variable yang temen-temen bisa gunakan untuk setting sonatype nexus-oss, diantaranya seperti berikut:

| Variable name                 | Example value       | Description |
| :---                          | :---                | :---        |


Dependencies
------------

None

Example Playbook
----------------

```ini
opensearch_cm      ansible_host=10.12.10.57   ansible_user=admin    ansible_port=22    os_node_roles="[cluster_manager]" opensearch_dashboard_enabled=true
opensearch_dt1     ansible_host=10.12.10.58   ansible_user=admin    ansible_port=22    os_node_roles="[data, ingest]"
opensearch_dt2     ansible_host=10.12.10.59   ansible_user=admin    ansible_port=22    os_node_roles="[data, ingest]"
```

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```ansible
- hosts: servers
  become: true
  vars:
    opensearch_version: 2.11.1
    default_admin_password: "Admin/4u@2024"
    opensearch_cluster_enabled: false # set to true if you want cluster mode
    opensearch_cluster_name: "logging_system"
  roles:
      - { role: dimmaryanto93.opensearch }
```

License
-------

MIT
