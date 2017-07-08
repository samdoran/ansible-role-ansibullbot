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
| `ansibullbot_user` | `ansibot` | User account that will run `ansibullbot` |
| `ansibullbot_group` | `{{ ansibullbot_user }}` | Group that `ansibullbot_user` belongs to. |
| `ansibullbot_clone_path` | `~{{ ansibullbot_user }}/ansibullbot` | Where to clone the `ansibullbot` git repository. |
| `ansibullbot_debug` | `True` | Whether or not to enable debugging. |
| `ansibullbot_github_username` | `ansibot` | GitHub account used for authenticating to the GitHub API. |
| `ansibullbot_github_password` | `''` | Password for authenticating to the GitHub. This should be stored in an Ansible Vault. |
| `ansibullbot_github_token` | `''` | GitHub API token used to talk to GitHub. This should be stored in an Ansible Vault. |
 | `ansibullbot_shippable_token` | `''` | Taken for talking to the Shippable API. This should be stored in an Ansible Vault. |
 | `ansibullbot_receiver_host` | `''` | Database where data is sent. |
 | `ansibullbot_receiver_port` | `''` | Database port. |

Dependencies
------------

- samdoran.repo-epel

Example Playbook
----------------

    - hosts: all
      roles:
         - samdoran.ansibullbot

License
-------

MIT
