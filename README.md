# ansible-zabbix-add

Add host to Zabbix

## Variables
`zabbix_admin_user: Admin` Admin user name

`zabbix_admin_password: zabbix` Admin user password

`zabbix_server: "127.0.0.1"` Zabbix server ip or hostname

`zabbix_server_https: false` Set to `true` if Zabbix server use https

`zabbix_proxy: ""` Zabbix proxy name

`zabbix_host_groups: "{{ group_names | difference('ungrouped') }}"` Groups to add host in zabbix to; defaults to host's ansible groups

`zabbix_hostname: "{{ inventory_hostname }}"` Hostname to use in zabbix while adding host, defaults to inventory hostname

`zabbix_host_ip: "{{ hostvars[inventory_hostname].ansible_host | default('0.0.0.0')  }}"` Host's IP to use in zabbix, defaults to 0.0.0.0

`zabbix_use_dns: true` If true, use dns name as host's interface, or else use IP

```
zabbix_host_templates:
  - "Template ICMP Ping"
  - "Template App SSH Service"
  - "Template OS Linux"
```
Basic zabbix templates

`zabbix_host_macros: []` Zabbix macros for host, must be a list of dictionaries. Example:
```
zabbix_host_macros:
  - name: TEST_MACRO
    value: TEST_VALUE
```



## Requirements
`zabbix-api` python module on host, where ansible is running from.


## Example Playbook
    - hosts: all
      roles:
        - role: ansible-zabbix-add
          zabbix_server: localhost


## License

MIT


## Author Information

Taras Bondarchuk
