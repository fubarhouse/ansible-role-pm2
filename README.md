# Ansible Role: PM2

[![Build Status](https://travis-ci.org/fubarhouse/ansible-role-pm2.svg?branch=master?style=for-the-badge)](https://travis-ci.org/fubarhouse/ansible-role-pm2)
[![Stability](https://img.shields.io/ansible/role/9715.svg?style=for-the-badge)](https://github.com/orangemug/stability-badges)
[![Releases](https://img.shields.io/github/tag/fubarhouse/ansible-role-pm2.svg?style=for-the-badge)](https://github.com/fubarhouse/ansible-role-pm2/releases)
[![Ansible Galaxy](https://img.shields.io/ansible/role/9715.svg?style=for-the-badge)](https://galaxy.ansible.com/fubarhouse/pm2)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)](https://raw.githubusercontent.com/fubarhouse/ansible-role-pm2/master/LICENSE)

* Install PM2 to any desired location - A node application manager
* Clone/Pull node applications from remote repositories
* Install node packages required for each specified application
* Copy configuration files
* Create databases
* Import database files
* Run initialization script
* Start application, and wait for response
* Flush logs

## Requirements

  As the URI module is in use here, Ansible v2.0.2 is required, however it will continue to work until ignore_errors is unset from that task.

## Role Variables

To cleanly install PM2, use `pm2_clean_install`.
````
pm2_clean_install: true
````

Configure each node application as an array item in `node_apps`.

This unique configuration is **required** by you, otherwise this role will not install any services into the PM2 daemon.

````
node_apps:
  - name: myApp
    port: 3000
    location: /opt/myapp
    start: app.js
    init: reset.js
    repository: ssh://git@bitbucket.org/mybitbucket/myapp.git
    database:
      name: myapp
      file: database.sql
    config:
      origin: config/local-example.js
      destination: config/local.js
````

## Dependencies

* None.

## Example Playbook

    - { role: fubarhouse.pm2 }

## Installation

* Add the PM2 role to your playbook.
* Modify above variables as desired.

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Karl Hepworth](https://twitter.com/fubarhouse).
