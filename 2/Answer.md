>Create one vm with 2 network interfaces one should behave as WAN and another as LAN. Create another vm attaching the previously created LAN interface to it.

- Created a CentOs VM with Host-Only and Bridged Network Interface.
    - Host-only interface has been assigned IP manually using cmd:
        > ifconfig ens37 10.10.3.2 netmask 255.255.255.0 up

- In similar way used Kali Linux as my client VM.
    > Assigned Host-only interface with ip add: 10.10.3.5/24

# In named below the task has been done.
    + CentOs WAN: 192.168.100.98
    + CentOs Host-only: 10.10.3.2/24


    + Kali Linux Host-only: 10.10.3.5/24


+ Figure: client_ifconfig.png = shows the ifconfig of Kali Linux.
+ Figure: host_ifconfig.png shows the if config of CentOs.
+ Figure ip_forward_png.png shows the ip_forward changed to 1 either in temporary or permanent way.

> Added the following command to route the packet from the ip add to the desired interface.
- Reference picture(firewall_routing_ip.png)

- firewall-cmd --permanent --direct --passthrough ipv4 -t nat -I POSTROUTING -o ens33 -j MASQUERADE -s 10.10.3.0/24

- firewall-cmd --change-interface=ens33 --zone=external --permanent 

- firewall-cmd --set-default-zone=internal
firewall-cmd --complete-reload

> After configuring the route from ens37 to ens33. We were able to ping the ip address as domain name couldn't be resolved.
- Reference Picture(twitter_ip_ping.png and ping_client_host_ip_router_ip.png)

> After the dns couldn't be resolved I checked out /etc/resolv.conf and nameserver was missing.

- So I added the line:
- - nameserver 8.8.8.8
