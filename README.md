# Ansible Role: Zap

[![Build Status](https://travis-ci.org/issmirnov/ansible-role-zap.svg?branch=master)](https://travis-ci.org/issmirnov/ansible-role-zap)

I'm automating my entire fleet using ansible. This role installs [zap](https://github.com/issmirnov/zap).

## Requirements

- On local machine: Working ansible installation
- On remote machine: `python` and `python-simplejson` for ansible to work.


## Role Variables

```
# Common:
zap_standalone: yes # installs with root privileges on port 80
zap_host: 127.0.0.1 # change to 0.0.0.0 for server installs
zap_port: 80 # change to 8927 if zap_standalone: no
zap_config: # default YAML config from https://github.com/issmirnov/zap/blob/master/c.yml

# OSX:
zap_config_location: /usr/local/etc/zap

# Ubuntu
zap_config_location: /etc/zap
zap_bin_path: /usr/local/bin


```

## Example Playbook

```
- hosts: servers
  vars:
    zap_config:
      e:
        expand: example.com
        a:
          expand: apples
      g:
        expand: github.com
        z:
          expand: issmirnov/zap
  roles:
    - { role: issmirnov.zap}
```

If you are provisioning a bare bones server, you can prepend this stanza to install core ansible dependencies automatically.

```
- name: install python on bare server
  remote_user: root
  hosts: all
  gather_facts: no
  pre_tasks:
    - name: 'install python2 and json support'
      raw: sudo apt-get -y install python-simplejson
```

## License

MIT

## Author Information

Ivan Smirnov, http://ivansmirnov.name
