# Ansible Role: PM2

[![Build Status](https://travis-ci.org/fubarhouse/ansible-role-pm2.svg?branch=master)](https://travis-ci.org/fubarhouse/ansible-role-pm2)

* Install PM2 to any desired location - A node application manager
* Clone/Pull node applications from remote repositories
* Install node packages required for each specified application
* Copy configuration files
* Create databases
* Import database files
* Run initialization script
* Start application, and wait for response
* Flush logs
* Create virtual hosts on Debian (apache2 and nginx)

## Requirements

  As the URI module is in use here, Ansible v2.0.2 is required, however it will continue to work until ignore_errors is unset from that task.


## Role Variables

To cleanly install PM2, use `pm2_clean_install`.
````
pm2_clean_install: true
````

Installation types include global, local and custom.
 - Global setting installs to `/usr/local/lib/node_modules/pm2`
 - Local setting installs to `~/.nvm/{{ node_version }}/lib/node_modules/pm2`
 - Custom setting installs to `{{ pm2_custom_path }}lib/node_modules/pm2`
 - If `"{{ pm2_install_type }}"` is not set to custom and `"{{ pm2_custom_path }}"` is not defined, `{{ pm2_install_type }}` will default to `global`.

Example:
````
pm2_install_type: custom
pm2_custom_path: /usr/local
````

Configure each node application as an array item in `node_apps`.

This unique configuration is required by you unless you use `node_apps: []`, otherwise this role **will** fail.

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

* Role: fubarhouse.nodejs

## Example Playbook

    - { role: fubarhouse.pm2 }

## Installation

* Add the PM2 role to your playbook.
* Modify above variables as desired.

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Karl Hepworth](https://twitter.com/fubarhouse).
