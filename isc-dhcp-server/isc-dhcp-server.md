# DHCP

### Installing DHCP Server

```
sudo apt-get update
apt-get install isc-dhcp-server -y
```

```
systemctl start isc-dhcp-server
systemctl enable isc-dhcp-server
systemctl status isc-dhcp-server
```

### Configuring DHCP Service

```
nano /etc/default/isc-dhcp-server
```

```
INTERFACESv4="eth0"
```

```
nano /etc/dhcp/dhcpd.conf
```

```
authoritative;

default-lease-time 660;
max-lease-time 6300;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.2 192.168.0.20;
  option routers 192.168.0.1
  option domain-name-servers 8.8.8.8;
  option domain-name "example.org";
  option broadcast-address 192.168.0.255;
}
```

### Configure DHCP Server to Assign Static IP to Client

```
nano /etc/dhcp/dhcpd.conf
```

```
host client {

hardware ethernet 4c:bb:58:9c:f5:55;

fixed-address 192.168.0.5;

}
```

### Restarting DHCP Server

```
systemctl restart isc-dhcp-server
systemctl status isc-dhcp-server
```

*tested*
