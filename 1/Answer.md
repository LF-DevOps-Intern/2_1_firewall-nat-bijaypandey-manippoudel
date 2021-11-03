>Create a virtual machine having the os centos.

Install firewall in the vm(centos might have firewall installed in default).(firewalld or iptables)

As firewall service may already be isntalled in our Linux System.

We can install it via:

-sudo yum install firewalld (Reference picture firewall_installation.png)



- - - Block certain ip range/subnet using firewalld.

>For blocking of ip range / subnet we can provide CIDR style network specification.

> Using IP tables 

- To block a certain ip address (Reference figure iptables_block_single_ip.png)
iptables -A INPUT -s 192.168.43.215 -j DROP 


- To block a range of IP address (Reference figure iptables_block_ip_range.png)
iptables -A INPUT -s 192.168.48.0/24 -j DROP

> Using firewalld (Reference figure firewalld_block_ip_range.png to apply command  and firewall_list_rule.png to list rules)

- firewall-cmd --add-rich-rule='rule family=ipv4 source address=192.168.48.0/24 reject' --permanent





> Allow http, https and ssh connection using firewall.

-To allow the services in firewall we can specify the services name in firewalld command (Reference figure firewall_allow_service_command.png).

- firewall-cmd --permanent --add-service=https
- firewall-cmd --permanent --add-service=http
- firewall-cmd --permanent --add-service=ssh




- To add these commands permanently we add --permanent in command.

You can add other rules as well as you prefer.
	Note: The firewall rules should be saved permanently.

