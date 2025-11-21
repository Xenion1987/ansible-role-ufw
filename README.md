# Ansible role: ufw

[![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/Xenion1987/ufw?label=Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/Xenion1987/ufw)
[![Ansible Galaxy](https://img.shields.io/badge/role-ufw-000000.svg?logo=ansible)](https://galaxy.ansible.com/xenion1987/ufw)
[![CI](https://github.com/xenion1987/ansible-role-ufw/actions/workflows/ci.yml/badge.svg)](https://github.com/xenion1987/ansible-role-ufw/actions/workflows/ci.yml)
[![License](https://img.shields.io/github/license/Xenion1987/ansible-role-ufw)](https://github.com/Xenion1987/ansible-role-ufw/blob/main/LICENSE)
[![Maintained](https://img.shields.io/badge/Maintained-yes-success.svg)](https://github.com/Xenion1987/ansible-role-ufw)
[![Molecule](https://img.shields.io/badge/tested%20with-Molecule-blue.svg)](https://github.com/ansible-community/molecule)

Install and configure `ufw` - Uncomplicated Firewall.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [ufw_allow_rfc1918_networks](#ufw_allow_rfc1918_networks)
  - [ufw_config](#ufw_config)
  - [ufw_config_file](#ufw_config_file)
  - [ufw_config_manage](#ufw_config_manage)
  - [ufw_default_rules](#ufw_default_rules)
  - [ufw_enabled](#ufw_enabled)
  - [ufw_host_rules](#ufw_host_rules)
  - [ufw_packages](#ufw_packages)
  - [ufw_service_name](#ufw_service_name)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.11`

## Default Variables

### ufw_allow_rfc1918_networks

Allow all access from RFC1918 networks:
- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

**_Type:_** bool<br />

#### Default value

```YAML
ufw_allow_rfc1918_networks: false
```

### ufw_config

Configuration object passed to the configuration file

**_Type:_** dict<br />

#### Default value

```YAML
ufw_config:
  IPV6: yes
  DEFAULT_INPUT_POLICY: DROP
  DEFAULT_OUTPUT_POLICY: ACCEPT
  DEFAULT_FORWARD_POLICY: DROP
  DEFAULT_APPLICATION_POLICY: SKIP
  MANAGE_BUILTINS: no
  IPT_SYSCTL: /etc/ufw/sysctl.conf
  IPT_MODULES: ''
```

### ufw_config_file

Path to the configuration file

**_Type:_** str<br />

#### Default value

```YAML
ufw_config_file: false
```

### ufw_config_manage

Whether to manage the configuration file

**_Type:_** bool<br />

#### Default value

```YAML
ufw_config_manage: false
```

### ufw_default_rules

List of rules to be applied.
see https://docs.ansible.com/ansible/latest/collections/community/general/ufw_module.html for more examples

**_Type:_** list<br />

#### Default value

```YAML
ufw_default_rules: []
```

#### Example usage

```YAML
ufw_default_rules_rules:
  - comment: Allow SSH
    rule: allow
    port: 22
    proto: tcp
  - comment: Delete rule 'Allow SSH'
    rule: allow
    port: 22
    proto: tcp
    delete: true
  - comment: Allow tcp 10000 - 11000
    rule: allow
    port: "10000:11000"
    proto: tcp
  - comment: Allow incoming access to eth0 from 1.2.3.5 port 5469 to 1.2.3.4 port 5469
    rule: allow
    interface: eth0
    direction: in
    proto: udp
    src: 1.2.3.5
    from_port: '5469'
    dest: 1.2.3.4
    to_port: '5469'
```

### ufw_enabled

Whether to Start the service and enable it on system boot

**_Type:_** bool<br />

#### Default value

```YAML
ufw_enabled: true
```

### ufw_host_rules

An additional list of rules which may be stored in 'group_vars' or 'host_vars'.
They will be set up in addition to the rules defined in 'ufw_default_rules'.

**_Type:_** list<br />

#### Default value

```YAML
ufw_host_rules: []
```

### ufw_packages

List of packages to install

**_Type:_** list<br />

#### Default value

```YAML
ufw_packages:
  - ufw
```

### ufw_service_name

Name of the service

**_Type:_** str<br />

#### Default value

```YAML
ufw_service_name: ufw
```

## Dependencies

None.

## License

BSD, MIT

## Author

[Xenion1987](https://github.com/Xenion1987)
