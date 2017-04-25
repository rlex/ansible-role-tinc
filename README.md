initially fork of https://github.com/thisismitch/ansible-tinc, has been expanded with new options and support for specifying tinc settings in hostvars and existing inventory, rather than in new separate group, which also allows usage with dynamic inventories.

Requires ansible >=2.2

Quickstart:
in host_vars/some_server:
```
tinc_vpn: present
tinc_vpn_hostname: internal_some_server
tinc_vpn_ip: 10.91.91.60
```

In group_vars/all (or whatever group you use)
```
tinc_netname: my_awesome_net
tinc_physical_ip: "{{ ipify_public_ip }}"
tinc_vpn_interface: tinc0
tinc_vpn_netmask: 255.255.255.0
tinc_vpn_subnet_cidr_netmask: 32
tinc_tcponly: 'yes'
tinc_iffonequeue: 'yes'
```

TBD: multiple network support, proper readme.
