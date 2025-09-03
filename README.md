# ansible-assignments

Lightweight Ansible example that installs a small set of packages on remote hosts using a role-based layout.

## What this repo does

Runs a playbook (`playbooks/main.yml`) that applies the `install_packages` role to one or more hosts defined in `inventory.ini`.

## Prerequisites

- Ansible (2.12+ recommended) installed locally.
- SSH/Password access to target hosts and appropriate privileges (become/sudo) when needed.
- A valid `inventory.ini` file with reachable hosts.

## Quick start

1. Edit `inventory.ini` to add your hosts. To pin the Python interpreter and avoid warnings, add per-host or per-group:

```
192.168.0.175 ansible_python_interpreter=/usr/bin/python3.11
```

2. Run the playbook (prompt for privilege escalation if required):

```
ansible-playbook playbooks/main.yml --inventory inventory.ini --ask-become
```

You can run in check/dry-run mode with `--check`.

## Repo layout

- `playbooks/main.yml` - top-level playbook that includes the role.
- `inventory.ini` - inventory of hosts/groups.
- `roles/install_packages/` - role that installs packages:
	- `tasks/main.yml` - install + logging tasks
	- `vars/main.yml` - package list

## Adding new Packages
 To add a new package, simply append a new dictionary to the `packages` list in `roles/install_packages/vars/main.yml` with the desired package name and state.

## License

This repository is provided as-is for learning and testing.
