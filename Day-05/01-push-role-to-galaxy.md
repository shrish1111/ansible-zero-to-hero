# Push your Ansible roles to Ansible Galaxy

1. Make sure your role is structured correctly. The basic structure should look like this:

```
my_role/
├── defaults/
│   └── main.yml
├── files/
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── templates/
├── tests/
│   ├── inventory
│   └── test.yml
└── vars/
    └── main.yml
```

2. Make sure ansible-galaxy CLI exists

```
ansible-galaxy --version
```

3. Push Your Role to GitHub

```
cd <role-name>
git init
git remote add origin <https://github.com/your_github_username/my_role.git>
git add .
git commit -m "Initial commit"
git push -u origin main
```

4. Import the Role to Ansible Galaxy

```
ansible-galaxy role import <your_github_username> <role-name>
```

This command will link your github to ansible -galaxy role

5. Get Role from Ansible Galaxy

```
ansible-galaxy install <github_username>.<role-name>
```
6. Some basic roles and collections commands

```
# Create a new role
ansible-galaxy init myrole

# Install a role from Galaxy
ansible-galaxy install geerlingguy.nginx

# Install a collection
ansible-galaxy collection install community.general

# Build and publish a collection
ansible-galaxy collection build
ansible-galaxy collection publish my_namespace-my_collection-1.0.0.tar.gz
```
