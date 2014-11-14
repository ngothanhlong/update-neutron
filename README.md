
- Lỗi máy VM không tải được gói cài đặt.
- Khi bị lỗi này VM ping từ trong ra ngoài và từ ngoài PING vào trong tốt.
- Nhưng VM bị stuck hoặc không thể nào SSH vào được.
- Nguyên nhân là do VM có MTU khi đi ra ngoài bị thừa 8 byte do GRE đóng gói vào.
- Việc này được thực hiện trên network node.
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
- Kill any existing dnsmasq processes:
```
killall dnsmasq
```
- Khởi động lại dịch vụ dhcp:

```
service neutron-dhcp-agent restart
```
