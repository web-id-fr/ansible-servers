# Ansible Servers

Recipes to install libraries, dependencies and dotfiles to Web^ID servers.

## Requirements

* Ansible 2.8.* : `brew install ansible`

## Setup

Copy `hosts.dist` to `hosts`:

```bash
cp hosts.dist hosts
```

Edit `hosts` accordingly, for example:

```ini
facebouc.web-id.coucou ansible_user=forge
twitaire.com ansible_user=forge
```

To test your hosts you can try:

```bash
ansible all -a "/bin/echo coucou" -i hosts
```

## Usage

To launch a playbook, for example `setup-ubuntu.yml`, on a single host (you will need the root password available):

```bash
ansible-playbook setup-ubuntu.yml -i hosts --limit=twitaire.com --ask-become-pass -u forge
```

Or if you're feeling lazy:

```bash
bin/ap setup-ubuntu.yml twitaire.com
```