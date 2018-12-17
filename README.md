
## Environment Setup

*requirement:*
- python2.7

MacOS
```
sudo /usr/bin/easy_install pip
sudo /usr/bin/python -m pip install linode-python
```

Ubuntu
```
python -m pip install linode-python
```

### verify environment in local

```
/usr/bin/python -c 'from linode import api'
```

### create a virtualenv

python2
```
python -m virtualenv venv
```

python3
```
python3 -m virtualenv venv
```

### use virtualenv

```
source venv/bin/activate
```

### install requirements

python2
```
pip install -r requirements.txt
```

python3
```
pip install -r requirements-py3.txt
```

### secret and vault files

```
.secret/
├── authorized_keys
├── linode-creation.yml
├── linode-credential.yml
└── linode-password
.vault/
└── secret_password
```

file name | purpose
----------|:-------
authorized_keys | users login by admin or deploy
linode-creation.yml | linode plan
linode-credential.yml | linode api key
linode-password | auto generate by bootstrap, and remeber to remove it if we want to change password
secret_password | for the vault file linode-credential.yml

### actions

* create linode server

```
ansible-playbook --vault-password-file=.vault/secret_password playbooks/bootstrap.yml
```

* keep the server information in 1password

* write the server ip in ./inventories/hosts after bootstrap

* server setup (haproxy and web server)

```
ansible-playbook playbooks/demo.yml
```
