paulrentschler.uWSGI
====================

[![MIT licensed][mit-badge]][mit-link]

Installs and configures the uWSGI daemon on Ubuntu Linux machines.

Requirements
------------

None.


Role Variables
--------------

The following variables are available with defaults defined in `defaults/main.yml`:

Install uWSGI to run in "emperor" mode.

    uwsgi_install_emperor: yes

Specify the version of Python that will be used (uses Python3 by default).

    uwsgi_use_python2: no
    uwsgi_use_python3: yes

**NOTE:** Ubuntu 18.04 is the last version that supports using Python 2 with uWSGI.


Specify the user and group that the uWSGI daemon runs as.

    uwsgi_user: www-data
    uwsgi_group: www-data


Try to automatically load plugins when unknown options are found.

    uwsgi_autoload: "true"

Enable the master process.

    uwsgi_master: "true"

Indicate how many workers/processes to spawn.

    uwsgi_workers: 2

Automatically kill workers if master dies (can be dangerous for availability).

    uwsgi_no_orphans: "true"

Prefix logs with date (can also specify a strftime string).

    uwsgi_log_date: "true"

Path to store the app config files.

    uwsgi_apps_path: /etc/uwsgi-emperor/apps

Trigger chain reload if the app config file is modified/touched.

    uwsgi_touch_chain_reload: "false"


Dependencies
------------

None.


Example Playbook
----------------

Simple version:

    - hosts: all
      roles:
        - paulrentschler.uwsgi


Use Python 2 and increase the number of workers:

    - hosts: all
      roles:
         - role: paulrentschler.ntp
           vars:
             uwsgi_use_python2: yes
             uwsgi_use_python3: no
             uwsgi_workers: 5


License
-------

[MIT][mit-link]


Author Information
------------------

Created by Paul Rentschler in 2021.


[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://github.com/paulrentschler/ansible-role-uwsgi/blob/master/LICENSE
