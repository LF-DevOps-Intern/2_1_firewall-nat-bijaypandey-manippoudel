>Create one vm with 2 network interfaces one should behave as WAN and another as LAN. Create another vm attaching the previously created LAN interface to it.

- Created a CentOs VM with Host-Only and Bridged Network Interface.
    - Host-only interface has been assigned IP manually using cmd:
        > ifconfig ens37 10.10.3.2 netmask 255.255.255.0 up

- In similar way used Kali Linux as my client VM.
    > Assigned Host-only interface with ip add: 10.10.3.5/24

# In named below the task has been done.
    + CentOs WAN: 192.168.1.119/24
    + CentOs Host-only: 10.10.3.2/24


    + Kali Linux Host-only: 10.10.3.5/24


+ Figure: client_ifconfig.png = shows the ifconfig of Kali Linux.
+ Figure: host_ifconfig.png shows the if config of CentOs.
+ Figure ip_forward_png.png shows the ip_forward changed to 1 either in temporary or permanent way.

