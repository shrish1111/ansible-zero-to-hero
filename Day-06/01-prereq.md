# Setup EC2 Collection and Authentication

## Install boto3

```
pip install boto3
```

## Install AWS Collection

```
ansible-galaxy collection install amazon.aws
```

## Setup Vault 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

Use a Vault password file

ansible-playbook playbook.yml --vault-password-file ~/.vault_pass.txt
Where ~/.vault_pass.txt is a file that contains only your Vault password (make sure it's secured).

✅ Example
Suppose you have:

vars/secret.yml (encrypted with Vault)

playbook.yml that includes:

- name: Example playbook using Vault
  hosts: all
  vars_files:
    - vars/secret.yml
  tasks:
    - name: Print secret variable
      debug:
        var: secret_token
You can run it using either of the methods above.

🔐 Encrypting a Variable File with Vault

ansible-vault encrypt vars/secret.yml

To edit:

ansible-vault edit vars/secret.yml

To decrypt temporarily:

ansible-vault view vars/secret.yml



