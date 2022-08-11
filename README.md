
# Ansible Role:  `knot-resolver`

This role will fully configure and install [knot-resolver](https://github.com/CZ-NIC/knot-resolver).

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/bodsch/ansible-icinga2/CI)][ci]
[![GitHub issues](https://img.shields.io/github/issues/bodsch/ansible-knot-resolver)][issues]
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/bodsch/ansible-knot-resolver)][releases]

[ci]: https://github.com/bodsch/ansible-knot-resolver/actions
[issues]: https://github.com/bodsch/ansible-knot-resolver/issues?q=is%3Aopen+is%3Aissue
[releases]: https://github.com/bodsch/ansible-knot-resolver/releases


## Requirements & Dependencies

not known

### Operating systems

Tested on

* ArchLinux
* Debian based
    - Debian 10 / 11
    - Ubuntu 20.04


## configuration

### default

```yaml
knot_resolver_support_ipv6: false

knot_resolver_listener: []

knot_resolver_systemd_instances: 2
knot_resolver_cachesize: 10

knot_resolver_internal_domain: []

knot_resolver_views: []
```

### listener

```yaml
knot_resolver_listener:
  - name: localhost
    interfaces:
      - eth0
    ips:
      - '127.0.0.1'
    port: 53
    options:
      tls: false
```


### internal domains

```yaml
knot_resolver_internal_domain:
  - domains:
      - 'molecule.lan'
      - 'matrix.lan'
      - '0.172.in-addr.arpa'
    policy:
      stub: '127.0.0.1@5353'
```

### views

```yaml
knot_resolver_views:
  - pass:
      - '127.0.0.0/8'
      - '192.168.0.0/24'
  - drop:
      - '0.0.0.0/0'
```

## Author and License

- Bodo Schulz

## License

[Apache](LICENSE)

`FREE SOFTWARE, HELL YEAH!`
