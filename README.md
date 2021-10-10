Ansible roles for docker swarm: consul
=========

Deploy consul to docker swarm.

[Consul](https://github.com/hashicorp/consul) is a distributed, highly available, and data center aware solution to connect and configure applications across dynamic, distributed infrastructure.

Requirements
------------

Docker must be installed and switched to swarm mode.

Role Variables
--------------

`consul_master_token`: when a master token is present within the Consul configuration, it is created and will be linked With the builtin Global Management policy giving it unrestricted privileges.

`consul_directory`: directory on the server for all consul files.

`consul_data_directory`: directory on the server for consul data.

`consul_docker_compose_file`: the path on the server where the `docker-compose.yml` file will be generated.

`consul_datacenter`: consul `datacenter` value.

`public_network_name`: the name of the public docker network to be created.

`consul_domain`: the domain name by which the consul will be available in the public network.

`consul_basic_auth`: login and password for basic authorization. All dollar signs in the hash need to be doubled for escaping. To create user:password pair, it's possible to use this command: `echo $(htpasswd -nb user password) | sed -e s/\\$/\\$\\$/g`


Dependencies
------------

Switch docker to swarm and create necessary networks manually or via role:
https://github.com/ansible-roles-for-docker-swarm/swarm

Example Playbook
----------------

```
- hosts: servers
  roles:
    - role: consul
      tags:
        - consul
```

License
-------

GPL-3.0-only

Author Information
------------------

Nothing.