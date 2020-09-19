# Info

Role to run Consul in container, as single instance or in cluster mode.

# Requirements

- Requires [Docker](https://www.docker.com/) to be installed.

# Usage

## Galaxy

`requirements.yml`

```
- name: agrrh.consul
  version: master  # Better place latest tag here
```

## Playbook

```
- role: agrrh.consul

  consul_version: 1.7.3

  consul_encrypt_string: changeme  # see defaults/main.yml

  consul_name: "{{ inventory_hostname }}"
  consul_dc: mydc
  consul_domain: consul

  consul_bind_addr: 0.0.0.0
  consul_client_addr: 0.0.0.0

  # consul_advertise_addr: "{{ ansible_all_ipv4_addresses | ipv4 | ipaddr('10.0.0.0/24') | first }}"

  consul_cluster:
    - consul1.example.org
    - consul2.example.org
    - consul3.example.org
```
