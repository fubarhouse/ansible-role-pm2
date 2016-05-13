# Ansible Role: PM2

  Install and manage NodeJs services/applications via PM2 and Ansible on Debian/Ubuntu servers.

  This role piggy-backs off the fubarhouse.npm role, which is an all-in-one solution for node version management.

  This role supports configuration file copy, database creation, initialisation/reset script execution and all on top of PM2 management.


## Requirements

  As the URI module is in use here, Ansible v2.0.2 is required, however it's not yet released on Brew.

  After version 2.0.2 or later has been made available via brew this message will be removed.

  In the interim, the URI task will not fail on error.

## Role Variables

  Copy the defaults/main.yml into the ansible system and add to the playbook, and change the variables accordingly.

  ````

  fubarhouse_pm2:
  pm2_exec: "/usr/local/bin/pm2"
  node_apps:
    - name: myApp
      database: myapp
      port: 3000
      location: /opt/myapp
      start: app.js
      init: reset.js
      repository: ssh://git@bitbucket.org/mybitbucket/myapp.git
      config:
        origin: config/local-example.js
        destination: config/local.js


  ````

## Dependencies

  * Role: fubarhouse.npm

## Example Playbook

  ```
    - { role: fubarhouse.pm2 }
  ```

## Installation

  * Add a copy of the defaults/main.yml into a new variables file included in the playbook, and plug in the details as required.

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Karl Hepworth](https://twitter.com/fubarhouse).
