[![Test deployment](https://github.com/GeekOops/geekoops-drupal/actions/workflows/CI.yml/badge.svg)](https://github.com/GeekOops/geekoops-drupal/actions/workflows/CI.yml)

# Set up Drupal

Configurable ansible role for installing drupal. webserver setup is separate.
We obtain drupal and dependencies via composer. A cronjob keeps them up-to-date.
mysql/mariadb is used for the database.

- openSUSE Leap 15.4 -> tested

## Role Variables
--------------

You can set the following variables to configure the role. Here listed are the variables and their default settings.


| Value | Description | Default |
|-------|-------------|---------|
|`sqlbackup` | file with an sql backup | "" |
|`drupal_location` | install location of drupal in /srv/www | "drupal9-hp" |
|`drupal_db_name` | name of mysql database | "drupal_hp" |
|`drupal_db_user` | mysql user | "drupal_user" |
|`drupal_db_pw` | password of mysql user | randomly generated? |
|`drupal_trusted_host_pattern` | A regex to trust certain hostnames, e.g. your own. | "^www\.example\.com$" |

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: jellyfish
      roles:
         - { role: geekoops-drupal, drupal_db_user: "drupal-user", drupal_db_pw: "1234abcd" }

An advanced example for the imaginary `jellyfish` test server

    - hosts: jellyfish
      roles:
         - role: geekoops-drupal
           vars:
             - drupal_db_user: "drupal-user"
             - drupal_db_pw: "1234abcd"

## Stuff to do afterwards
- If you replayed a backup, you need to copy over files, modules, themes...
- set up cron-job for drupal cron

## License

MIT

## Development
- extend to setup the webserver. Currently we don't provide a vhost for it.
- Test on 15.3
