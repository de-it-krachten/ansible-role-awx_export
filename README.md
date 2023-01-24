[![CI](https://github.com/de-it-krachten/ansible-role-awx_export/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-awx_export/actions?query=workflow%3ACI)


# ansible-role-awx_export

export AWX configuration into JSON



## Dependencies

#### Roles
None

#### Collections
- community.general
- awx.awx:21.7.0

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8<sup>1</sup>
- RockyLinux 9<sup>1</sup>
- OracleLinux 8
- OracleLinux 9<sup>1</sup>
- AlmaLinux 8<sup>1</sup>
- AlmaLinux 9<sup>1</sup>
- Debian 11 (Bullseye)<sup>1</sup>
- Ubuntu 20.04 LTS<sup>1</sup>
- Ubuntu 22.04 LTS<sup>1</sup>
- Fedora 37<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Use non default virtual env
# awx_python_interpreter: /virtenv/awx/bin/python3

# Full path to the awxkit / awx command
awx_command: awx

# Host to execute code from
awx_execution_host: localhost

# AWX url
awx_url: https://127.0.0.1

# AWX username to use
awx_username: admin

# AWX password to use
awx_password: admin

# Should SSL/TLS verification be done
awx_verify_ssl: false

# Location where to export files to
# awx_export_path: /tmp/awx

# List of resources to export
awx_export_resources:
  - settings
  - credential_types
  - credentials
  # - execution_environments
  - inventory
  - inventory_sources
  - job_templates
  - notification_templates
  - organizations
  - projects
  - teams
  - users
  - workflow_job_templates
  - roles
  - schedules
  - applications
  - system_job_templates
  - groups
  - hosts
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'awx_export' pre playbook
  ansible.builtin.import_playbook: converge-pre.yml

- name: sample playbook for role 'awx_export'
  hosts: all
  become: "no"
  vars:
    awx_command: /usr/local/bin/awx
    awx_export_path: /tmp/awx
  tasks:
    - name: Include role 'awx_export'
      ansible.builtin.include_role:
        name: awx_export
</pre></code>
