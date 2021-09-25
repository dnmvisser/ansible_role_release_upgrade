# Upgrade to specific OS release

Fully automated upgrading of a Debian system to a specific major version, including intermediate reboots.

Supported upgrade paths start at Debian 8 (jessie), and defaults to upgrading to
Debian 11 (bullseye).

The role will run all the required upgrades in sequence, so:

- Debian 8 systems will go to 9, 10, and end up at Debian 11.
- Debian 9 will go to 10, and then to Debian 11.
- etc

It is also possible to upgrade to an earlier release, for example:

- Debian 9 to Debian 10.

Downgrading is not supported.


This role was created to automate the upgrade of VMs on a platform that only
offered instantiating Debian 9 VMs.
It has been tested on clean VMs only.

# Example Playbook

```yaml
# Run two upgrades in sequence, to become Debian 11
- hosts: stretch
  roles:
    - role: ansible_role_release_upgrade
```

```yaml
# Upgrade Debian 8 to Debian 11, which means three consequetive upgrades:
# - 8 to 9
# - 9 to 10
# - 10 to 11
#
- hosts: jessie
  roles:
    - role: ansible_role_release_upgrade
```


```yaml
# Upgrade Debian 9 to Debian 10
- hosts: stretch
  roles:
    - role: ansible_role_release_upgrade
      vars:
        required_release_version: 10
```

Author Information
------------------

Dick Visser
