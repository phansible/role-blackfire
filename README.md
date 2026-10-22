# Phansible Role: Blackfire

[![CI](https://github.com/phansible/role-blackfire/actions/workflows/ci.yml/badge.svg)](https://github.com/phansible/role-blackfire/actions/workflows/ci.yml)

An Ansible Role that installs the [Blackfire](https://blackfire.io/) agent and PHP probe from the official Blackfire apt repository, specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

- Ubuntu 22.04, 24.04, 26.04 or Debian 12, 13
- Ansible >= 2.15
- PHP installed by [role-php](https://github.com/phansible/role-php) earlier in the same play (its `restart php-fpm` handler is used)

## Role Variables

```yaml
blackfire_server_id: ''
blackfire_server_token: ''
```

- `blackfire_server_id` (default `''`): server ID from your Blackfire account.
- `blackfire_server_token` (default `''`): server token from your Blackfire account.

The agent is configured and started only when both are set. Keep them in Ansible Vault or another secret store, not in plain text.

## Dependencies

[role-php](https://github.com/phansible/role-php), listed before this role in the play.

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
    php_version: "8.4"
    blackfire_server_id: "{{ vault_blackfire_server_id }}"
    blackfire_server_token: "{{ vault_blackfire_server_token }}"
  roles:
    - role-php
    - role-blackfire
```

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-blackfire/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-blackfire/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
