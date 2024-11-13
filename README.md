Ansible Gremlin Role
========

Install and configure Gremlin

Supports most Debian and RHEL-based Linux distros

Installation
------------

```
ansible-galaxy install -v git+https://github.com/gremlin/ansible-gremlin.git,master,Gremlin.gremlin
```

Role Variables
--------------

- `gremlin_team_id` - Your Team ID (required for authentication)
- `gremlin_team_secret` - Your Team Secret (should only require secret or PEM certificates, not both)
- `gremlin_team_private_key_or_file` - Your PEM-encoded private key or path/filename to a file containing the private key (required for authentication)
- `gremlin_team_certificate_or_file` - The PEM-encoded public-key certificate or path/filename to the file containing your PEM-encoded public-key certificate (required for authentication)
- `gremlin_identifier` - Custom name for this client (default as the host's IP address)
- `gremlin_client_tags` - Comma-separated list of custom tags to assign to this client (e.g. GREMLIN_CLIENT_TAGS="zone=us-east1,role=mysql,foo=bar")
- `http_proxy` - In the form http[s]://[username:passsword@]address:port
- `https_proxy` - In the form http[s]://[username:passsword@]address:port
- 'service_discovery' - If specified, will enable Service Discovery.


Dependencies
------------
None

Example Playbooks
-----------------


With TeamID & Secret

```yaml
---

- hosts: localhost
  roles:
     - { role: Gremlin.gremlin, become: yes}
  vars:
    gremlin_config:
      gremlin_team_id: 9999999a-888b-777c-666d-55555555555e
      gremlin_team_secret: 1111111f-222e-333d-444c-55555555555d
```

With Private Key authentication
```yaml
---

- hosts: localhost
  roles:
     - { role: Gremlin.gremlin, become: yes}
  vars:
    gremlin_config:
      gremlin_team_id: 9999999a-888b-777c-666d-55555555555e
      gremlin_team_private_key_or_file: "file:///var/lib/gremlin/key.pem"
      gremlin_team_certificate_or_file: "file:///var/lib/gremlin/cert.pem"
```


License
-------

Apache2

Author Information
------------------

kyle@gremlin.com

Version
-------
v0.2 (Beta)
