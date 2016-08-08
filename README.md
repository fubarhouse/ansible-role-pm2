# Ansible Role: PM2

[![Build Status](https://travis-ci.org/fubarhouse/fubarhouse.pm2.svg?branch=master)](https://travis-ci.org/fubarhouse/fubarhouse.pm2)

* Install PM2 - A node application manager
* Clone/Pull node applications from remote repositories
* Install node packages required for each specified application
* Copy configuration files
* Create databases
* Import database files
* Run initialization script
* Start application, and wait for response
* Flush logs
* Create virtual hosts

## Requirements

  As the URI module is in use here, Ansible v2.0.2 is required, however it will continue to work until ignore_errors is unset from that task.


## Role Variables

Configure each node application as an array item in `node_apps`.

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

## Dependencies

* Role: fubarhouse.npm

## Example Playbook

    - { role: fubarhouse.pm2 }

## Installation

* Add the PM2 role to your playbook.
* Modify above variables as desired.

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Karl Hepworth](https://twitter.com/fubarhouse).
