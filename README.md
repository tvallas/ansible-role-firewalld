Ansible role firewalld
=========

Manages firewalld firewall rules

Requirements
------------

firewalld

Role Variables
--------------
##### `firewalld_enabled` (optional)

defines if firewalld is enabled (boolean, by default true)

##### `firewalld_services` (optional)


Defines values for firewalld_services:

    firewalld_allow_services:
      service: <service name>
      zone: [zone] (default: public)
      permanent: [True|False] (default: True)
      immediate: [True|False] (default: True)
      state: [enabled|disabled]	(default: enabled)

Only service is required!

**Note that ssh service is always allowed by this role
to prevent misconfigurations!**

##### `firewalld_ports` (optional)

Defines values for firewalld_ports:

    firewalld_ports:
      port: <port/protocol>
      zone: [zone] (default: public)
      permanent: [True|False] (default: True)
      immediate: [True|False] (default: True)
      state: [enabled|disabled]	(default: enabled)

#### `firewalld_rich_rules` (optional)

    firewalld_rich_rules:
      rich_rule: <rich_rule>
      zone: [zone] (default: public)
      permanent: [True|False] (default: True)
      immediate: [True|False] (default: True)
      state: [enabled|disabled]	(default: enabled)


Example Playbook
----------------

    - hosts: servers
      vars:
        firewalld_services:
          - { service: "http" }
          - { service: "telnet", zone: "dmz", permanent: True, state: "disabled" }
      roles:
        - firewalld



License
-------
MIT


Author Information
------------------
Tuomas Vallaskangas
