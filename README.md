ansible-role-docker
=========

# Table of Contents

- [Description](#description)
- [Requirements](#requirements)
- [Role variables](#role variables)
- [Examples](#examples)

Ansible role to install and configure Docker Daemon.
The official Docker repository will be added to the package manager and files be installed from there.

Supported operating systems:
- RHEL 6/7
- Ubuntu Precise/Trusty

# Requirements

- Ansible >= 2.0
- If using CentOS 6 [EPEL] repository must be available.

# Role Variables

| Name | Description | Value |
| :------ | :-------------- | :------ |
| docker_data_dir | Specify the directory Docker will use | /var/lib/docker |
| docker_package_name | Package name | docker-engine |
| docker_package_state | State of Docker package | installed |
| docker_service_name | Name of Docker service used by SysV/Systemd | docker |
| docker_service_state | State of Docker service | running |
| docker_service_enabled | Should Docker service start on boot | true |
| docker_repository_url | URL of Docker's yum repo | https://yum.dockerproject.org/repo/main/centos/{{ ansible_distribution_major_version }} |
| docker_repository_template_file | Name of template to use for repo | docker.repo.j2 |
| docker_config_template_file | Name of template to use for dropin config (7.x only) | docker.dropin.j2 |
| docker_config_path | Path to config file (7.x only) | /etc/systemd/system/docker.service.d |
| docker_config_file | Additional docker config (7.x only) | {{ docker_config_path }}/overrideexec.conf
| docker_options | Options to add to docker deamon (7.x only) | --insecure-registry 10.0.0.0/8 --exec-opt native.cgroupdriver=cgroupfs |
| docker_flush_handlers | Boolean to define if handlers should be flushed | false |

# Dependencies

None

# Tags
- docker_install: ensure that all packages in __docker_package_name__ are in state __docker_package_state__
- docker_config: ensure configuration
- docker_service: ensure that all services in __docker_service_name__ are in state __docker_service_state__

# Examples
```yaml
- hosts: docker-servers
  become: true
  become_method: sudo
  become_user: root
  roles:
  - role: docker
```

# License

BSD

# Author Information

[Thomas Krahn](mailto:ntbc@gmx.net)
