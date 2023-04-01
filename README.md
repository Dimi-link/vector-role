vector-role
=========

A role for vector installation and configuration

Requirements
------------

Not defined

Role Variables
--------------

vector configuration path
```bash
vector_config_dir: "/etc/vector"
```
enable or disable vector API status
```bash
api_enabled: false
```
vector API listen address binding
```bash
listen_address: 127.0.0.1:8686
```
vector sources
```bash
sources:
  - name: dummy_logs
    config:
      type: demo_logs
      format: syslog
      interval: 1
```
vector sinks
```bash
sinks:
  - name: my_sink_id
    config:
      type: console
      inputs:
      - dummy_logs
      target: stdout
      encoding:
        codec: json
```
Dependencies
------------

Not required

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      pre_tasks:
      roles:
        - role: vector-role
          vars:
            api_enabled: true
            listen_address: 127.0.0.1:8686
            sources:
              - name: dummy_logs
                config:
                  type: demo_logs
                  format: syslog
                  interval: 1
            sinks:
              - name: my_sink_id
                config:
                  type: console
                  inputs:
                  - dummy_logs
                  target: stdout
                  encoding:
                    codec: json

License
-------

BSD