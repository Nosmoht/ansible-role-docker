ansible-role-docker
=========

# Table of Contents

- [Description](#description)
- [Requirements](#requirements)
- [Role variables](#role variables)
- [Examples](#examples)

Ansible role to install and configure Docker Daemon on RHEL based systems.
A yum repo file will be created in /etc/yum.repos.d which uses the official
Docker yum repository to install docker.

# Requirements

If using CentOS 6 [EPEL] repository must be available.

# Role Variables

| Name | Description | Value |
| :------ | :-------------- | :------ |
| docker_data_dir | Specify the directory Docker will use | /var/lib/docker |
| docker_package_name | Package name | docker-engine |
| docker_package_state | State of Docker package | installed |
| docker_service_name | Name of Docker service used by SysV/Systemd | docker |
| docker_service_state | State of Docker service | running |
| docker_service_enabled | Should Docker service start on boot | true |
| docker_yum_repo_url | URL of Docker's yum repo | https://yum.dockerproject.org/repo/main/centos/{{ ansible_distribution_major_version }} |
| docker_yum_repo_template_file | Name of template to use for repo | docker.repo.j2 |

# Dependencies

None

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
