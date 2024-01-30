# Ansible Role: CorkScrew

The Ansible Role for install **corkscrew** on Debian/Ubuntu.
Proxying an SSH connection via an HTTP proxy

## Requirements

None.

## Example

```yaml
# Vars
corkscrew_config:
  - user: ubuntu # For which user configuring
    hosts:
      - name: 'github.com'      # GIT server hostname
        proxy_addr: 127.0.0.1 # proxy server address
        proxy_port: 8080        # proxy server port
        forward_agent: yes      # OPTIONAL: forward ssh agent (default: yes)
        proxy_user: ''          # OPTIONAL: proxy server user (default: '')
        proxy_password: ''      # OPTIONAL: proxy server password (default: '')
      - name: 'gitlab.com'
        proxy_addr: 127.0.0.1
        proxy_port: 8080
      - name: 'bitbucket.org'
        proxy_addr: 127.0.0.1
        proxy_port: 8080

# Playbook
tasks:
  - name: corkscrew install
    hosts: all
    roles:
      - role: corkscrew
```

## Role Variables

| Variable               | Default            | Description                            |
|------------------------|--------------------|----------------------------------------|
| corkscrew_apt_pkg_name | corkscrew          | APT package name                       |
| corkscrew_config       | []                 | List of hosts for which enable a proxy |
| corkscrew_execute_path | /usr/bin/corkscrew | Path to the corkscrew executable file  |
