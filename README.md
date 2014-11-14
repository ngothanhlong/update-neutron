update-neutron
==============
- Sửa file này :
```
/etc/neutron/dhcp_agent.ini
[DEFAULT]
...
dnsmasq_config_file = /etc/neutron/dnsmasq-neutron.conf
```
- Tạo file /etc/neutron/dnsmasq-neutron.conf 
```
dhcp-option-force=26,1454
```
Kill any existing dnsmasq processes:
```
killall dnsmasq
```
Khởi động lại dịch vụ dhcp:

```
service neutron-dhcp-agent restart
```
