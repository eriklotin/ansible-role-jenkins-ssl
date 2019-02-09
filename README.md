# Ansible role: eriklotin.jenkins-ssl
This role installs docker, nginx proxy, jenkins and let's encrypt certificate.

# Install
```
ansible-galaxy install eriklotin.jenkins-ssl
```
or install locally:
```yaml
ansible-galaxy install eriklotin.jenkins-ssl -p ./roles/
```

# Variables

List of system users which will be added to docker system group.
```yaml
docker_users: []
```

Working directory. `jenkins` in home directory by default. Will created by role.
```yaml
jenkins_workdir: "{{ ansible_env.HOME }}/jenkins"
```

Your domain. Already must point to host. (required)
```yaml
jenkins_domain: 'example.com'
```

Your valid email address for Let's Encrypt. (required)
```yaml
jenkins_domain_admin_email: 'admin@example.com'
```

# Example playbook

```yaml
- hosts: all

  vars:
    - docker_users: ["ubuntu"]
    - jenkins_domain: "example.com"
    - jenkins_domain_admin_email: "admin@example.com"

  roles:
    - role: eriklotin.jenkins-ssl
```

# Dependencies

This role uses [eriklotin.nginx](https://github.com/eriklotin/ansible-role-nginx) role to install Docker 
and NGINX.


# License
MIT. See `LICENSE` file.

# Author
Created in 2019-02 by [Erik Lotin](https://github.com/eriklotin).