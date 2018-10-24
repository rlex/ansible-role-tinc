##### Description
Installs and configures tinc mesh vpn.  
Also synchronizes keys between nodes.  
Requires ansible >=2.5

Example playbook:

```
- name: install and configure tinc mesh VPN
  hosts: all
  any_errors_fatal: true
  roles:
    - { role: tinc, tags: tinc }
```

##### Quickstart:
in host_vars/some_server:
```
tinc_vpn: present
tinc_vpn_hostname: internal_some_server
tinc_vpn_ip: 10.91.91.60
```

In group_vars/all (or whatever group you use)
```
tinc_netname: my_awesome_net
tinc_vpn_interface: tinc0
tinc_vpn_netmask: 255.255.255.0
tinc_vpn_subnet_cidr_netmask: 32
tinc_tcponly: 'yes'
tinc_iffonequeue: 'yes'
```

##### Ipify
If your server is behind NAT (not so rare case) you might need to get public ip from ipify.  
In that case, default setting (ansible_default_ipv4["address"]) will return LAN ip  
To use ipify for getting public IP, set 
```
tinc_physical_ip: "{{ ipify_public_ip }}"
tinc_use_ipify: true
```
In host/group vars.

##### Credits

[Mitchell Anicas](https://github.com/thisismitch/ansible-tinc) for initial version