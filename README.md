Ansible Swag (Docker)
=========
[![CI](https://github.com/warhorse/ansible-role-swag-docker/workflows/CI/badge.svg?event=push)](https://github.com/warhorse/ansible-role-swag-docker/actions?query=workflow%3ACI)
[![warhorse.swag_docker](https://img.shields.io/ansible/role/57577)](https://galaxy.ansible.com/warhorse/swag_docker)
[![warhorse.swag_docker](https://img.shields.io/ansible/quality/57577)](https://galaxy.ansible.com/warhorse/swag_docker)
[![warhorse.swag_docker](https://img.shields.io/ansible/role/d/57577)](https://galaxy.ansible.com/warhorse/swag_docker)
![License](https://img.shields.io/github/license/warhorse/ansible-role-swag-docker)
![Commit](https://img.shields.io/github/last-commit/warhorse/ansible-role-swag-docker)



Install Swag (Docker)

This role is part of the Warhorse Automation Framework. This role can be used with Warhorse or as a standalone role.

Docker Image
-------------

[swag](https://github.com/linuxserver/docker-swag)

Role Variables
--------------

A list of all the variables can be found in ./defaults/main.yml.

swag_hostname: "swag"
swag_container_name: "swag"
swag_docker_version: "latest"

swag_dns_plugin: 'digitalocean'
swag_domain_name: 'example.com'

swag_docker_labels: {}
swag_docker_image: "linuxserver/swag:{{ swag_docker_version }}"
swag_docker_network: "swag"
swag_network_ipam_temp: "{{ swag_network_ipam | default({}) }}"
swag_network_ipam_subnet: "{{
  swag_network_ipam_temp.subnet
  | default('172.16.1.0/24')
}}"
swag_network_ipam_gateway: "{{
  swag_network_ipam_temp.gateway
  | default('172.16.1.1')
}}"
swag_network_ipam_iprange: "{{
  swag_network_ipam_temp.iprange
  | default('172.16.1.0/24')
}}"

swag_dir: '/opt/docker/swag'
swag_data_dir: '/config'
swag_ports:
  - "80:80"
  - "443:443"


Dependencies
------------

```shell
ansible-galaxy install geerlingguy.docker geerlingguy.pip
```

Install
------------

```shell
ansible-galaxy install warhorse.swag_docker
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
      - { role: warhorse.swag_docker }
```

License
-------

MIT/BSD

Author Information
------------------

Ralph May
