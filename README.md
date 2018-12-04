Ansibullbot
=========
[![Galaxy](https://img.shields.io/badge/galaxy-samdoran.ansibullbot-blue.svg?style=flat)](https://galaxy.ansible.com/samdoran/ansibullbot)
[![Build Status](https://travis-ci.org/samdoran/ansible-role-ansibullbot.svg?branch=master)](https://travis-ci.org/samdoran/ansible-role-ansibullbot)

Install [Ansibullbot](https://github.com/ansible/ansibullbot), your friendly neighborhood GitHub assistant.

Requirements
------------

GitHub and Shippable credentials with appropriate permissions. This doesn't do much good unless the credentials have acces to the [Ansible](https://github.com/ansible/ansible) GitHub repository.

Role Variables
--------------

| Name              | Default Value       | Description          |
|-------------------|---------------------|----------------------|
| `ansibullbot_action` | `install` | Set of tasks to run. Options are `install` and `update`. |
| `ansibullbot_user` | `ansibot` | User account that will run `ansibullbot` |
| `ansibullbot_group` | `{{ ansibullbot_user }}` | Group that `ansibullbot_user` belongs to. |
| `ansibullbot_repo_url` | `https://github.com/ansible/ansibullbot` | URL of the ansibullbot git repo. |
| `ansibullbot_home_dir` | `/home/{{ ansibullbot_user }}` | Where to create home directory for Ansibullbot user. |
| `ansibullbot_clone_path` | `{{ ansibullbot_home_dir }}/ansibullbot` | Where to clone the `ansibullbot` git repository. |
| `ansibullbot_log_path` | `/var/log/ansibullbot.log` | Path to log file. |
| `ansibullbot_cache_dir` | `{{ ansibullbot_home_dir }}/.ansibullbot/cache/shippable.runs/.raw` | Where cache files are stored. Used for cleaning up old cache files. |
| `ansibullbot_enable_receiver` | `false` | Whether or not to enaable the `ansibullbot_receiver` service. Requires  |
| `ansibullbot_cache_days_to_keep` | `30` | How many days wort of cache files to keep. |
| `ansibullbot_debug` | `True` | Whether or not to enable debugging. |
| `ansibullbot_github_username` | `ansibot` | GitHub account used for authenticating to the GitHub API. |
| `ansibullbot_github_password` | `''` | Password for authenticating to the GitHub. This should be stored in an Ansible Vault. |
| `ansibullbot_github_token` | `''` | GitHub API token used to talk to GitHub. This should be stored in an Ansible Vault. |
 | `ansibullbot_shippable_token` | `''` | Taken for talking to the Shippable API. This should be stored in an Ansible Vault. |
 | `ansibullbot_receiver_host` | `''` | Database where data is sent. |
 | `ansibullbot_receiver_port` | `''` | Database port. |
 | `ansibullbot_packages` | [see `defaults/main.yml`] | List of packages to install. |
 | `ansibullbot_slack_message` | `Updating Ansibullbot` | Message posted to Slack when updating Anisbullbot. |
 | `ansibullbot_slack_token` | `[]` | Slack API toke. This should be stored in an Ansible Vault. |
 | `ansibullbot_sentry_url` | `~` | URL of the Sentry server. |
 | `ansibullbot_sentry_env` | `prod` | Sentry environment |
 | `ansibullbot_sentry_trace` | `true` | Whether or not to collect trace information and send to Sentry. |

Dependencies
------------

- samdoran.repo-epel

Example Playbook
----------------

    - hosts: all
      roles:
          - samdoran.repo-epel
          - samdoran.firewall
          - samdoran.fail2ban
          - samdoran.ansibullbot

License
-------

MIT
