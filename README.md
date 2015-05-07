Role Name
=========

Ansible role to install and configure Docker on RHEL based systems.

# Requirements

If using CentOS 6 [EPEL] repository must be available.

# Role Variables

| Name | Description | Value |
| :------ | :-------------- | :------ |
| docker_data_dir | Specify the directory Docker will use | /var/lib/docker |
| docker_package_state | State of Docker package | installed |
| docker_packages | List of Packages to install Docker | Depends on {ansible_distribution_major} RHEL6=docker-io, RHEL7=docker
| docker_service_name | Name of Docker service used by SysV/Systemd | docker |
| docker_service_state | State of Docker service | running |
| docker_service_enabled | Should Docker service start on boot | true |

# Dependencies

None

# Example Playbook
```yaml
- hosts: docker-servers
  roles:
  - role: docker
```

# License

BSD

# Author Information

[Thomas Krahn]

[EPEL]: https://fedoraproject.org/wiki/EPEL
[Thomas Krahn]: mailto:ntbc@gmx.net
