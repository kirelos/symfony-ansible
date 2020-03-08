# Symfony Ansible
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0) [![Galaxy](https://img.shields.io/badge/galaxy-kirelos.symfony__ansible-blue.svg)](https://galaxy.ansible.com/kirelos/symfony_ansible)

Automated deployment for symfony application using ansible on `Debian 9`, `Ubuntu 18.04` and newer releases.

## What this script is really do:
1. Add A record on Cloudflare DNS.
2. Symfony project deployment.
4. Create PHP-FPM pool for your application.
4. NGINX configuration for your application.

## Requierments
1. This playbook tested on Ansible 2.9
2. This Script only works on Ubuntu or Debian only (For Now).
3. PHP-FPM
4. NGINX
5. MySQL

Note: this playbook tested on Symfony 4 project.

## Installation

### Install from Ansible Galaxy
```sh
ansible-galaxy install kirelos.symfony_ansible
```

## Variables
Please change the variables before using this playbook `vars/vars.yml`

| variable          | Description |
| ------------      | ----------- |
| `domain`          | Your Main domain name.|
| `host`            | You Sub-domain to access the application.|
| `sym_user`        | Application user name.|
| `repo`            | Your project git repo.|
| `branch`          | Your project git branch you want to use.|
| `path`            | Application path on your server.|
| `mysql_host`      | MySQL server host.|
| `mysql_port`      | MySQL server port.|
| `sym_db_host`     | MySQL client host.|
| `sym_db_name`     | MySQL database name.|
| `sym_db_user`     | MySQL database user.|
| `sym_db_password` | MySQL database password.|
| `php_version`     | PHP version you will use.|
| `cf_api_key`      | CLoudflare api key.|
| `cf_api_email`    | CLoudflare api email.|
| `enable_cf`       | Enable CLoudflare proxy yes or no.|
| `installer`       | Installer path.|
| `symfony`         | Symfony commands path.|
| `cache_path`      | Symfony cache folder path.|
| `logs_path`       | Symfony logs folder path.|

## Start your Deployment
1. After setting your variable
2. add app private key `roles/symfony/templates/id_rsa` that has access on your project repo.

### Run Ansible playbook
```sh
ansible-playbook -i hosts_inventory deploy_symfony.yml
```