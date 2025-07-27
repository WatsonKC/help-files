# Configure BIND Master DNS Server on Debian 11 / Debian 10 | ComputingForGeeks
If you have a domain name and would like to have your own DNS server to handle name resolution for your domain name instead of using your domain registrar’s DNS server, then you definitely require to set up an authoritative server. An authoritative DNS server is used to store DNS records by domain owners and provides answers to DNS resolvers such as 8.8.8.8 0r 1.1.1.1.

A **Domain Name System** abbreviated as DNS is an internet service used to resolve Domain Name to an IP Address and vice-versa. **BIND**(Berkeley Internet Name Domain) is an open-source, flexible, and full-featured DNS software that can be used to act as an authoritative DNS server. It provides the functionality of the Domain Name to IP Address conversion.

This guide will help you configure Master BIND DNS Server on Debian 11 / Debian 10. Ensure that your server has a static IP Address if you are using DHCP, you will have to configure it to static to declare that no changes to your IP will happen after the DNS Server is set.

Step 1 – Install Bind DNS Server
--------------------------------

Before we begin on the installation, it is always safe to update your Debian 11 / Debian 10 repository index. This is achieved by executing the below command.

```
sudo apt update -y
```


Then proceed and install the BIND DNS server. The name for this DNS server in Debian is bind9 and is available in the default base repository. Install it using the APT command as below

```
sudo apt-get install -y bind9 bind9utils bind9-doc dnsutils
```


Step 2 – Configure Bind Master DNS Server
-----------------------------------------

The configuration directory of bind9 is **/etc/bind/**. It holds both configurations files and Zone lookup files. The global configuration is **/etc/bind/named.conf** which is not used for local DNS configuration, instead **/etc/bind/named.conf.local** is used.

### Create Zones

Using the **/etc/bind/named.conf.local** file, we will create zones by editing the contents of this file using an editor of your choice. Install vim editor using `sudo apt install vim`

```
sudo vim /etc/bind/named.conf.local
```


We will create both the forward and reverse zones. First, let’s start by creating an entry for the forward zone for _computingforgeeks.local_ domain. Replace this domain name with your set domain name.

```
zone "computingforgeeks.local" IN { // Domain name
    
      type master; // Primary DNS

     file "/etc/bind/forward.computingforgeeks.local.db"; // Forward lookup file

     allow-update { none; }; // Since this is the primary DNS, it should be none.

};
```


In the above file, **_forward.computingforgeeks.local.db_** is the name of your forward lookup zone.

Now let us create the forward zone for **_computingforgeeks.local_**. In the same file, add the below lines replacing accordingly with your parameters as in the forward zone.

```
zone "1.168.192.in-addr.arpa" IN { //Reverse lookup name, should match your network in reverse order

     type master; // Primary DNS

     file "/etc/bind/reverse.computingforgeeks.local.db"; //Reverse lookup file
 allow-update { none; }; //Since this is the primary DNS, it should be none.

};
```


In the above file, **_1.168.192.in-addr.arpa_** is the name of the reverse DNS (if your network is 172.16.10 then it will be reversed to 10.16.172 and _**reverse.computingforgeeks.local.db**_ is the reverse DNS lookup file.

Step 3 – Configure Bind DNS zone lookup files
---------------------------------------------

The lookup zones hold the DNS records for both the forward and reverse zones.

First, let’s create the forward zone lookup file. We will copy the sample zone lookup file called **forward.computingforgeeks.local.db** as below.

```
sudo cp /etc/bind/db.local /etc/bind/forward.computingforgeeks.local.db
```


Remember that there is syntax, and domain names end with a dot (.)

Also, there are acronyms that we need to understand.

*   **SOA** – Start of Authority
*   **A** – A record
*   **MX** – Mail for Exchange
*   **NS** – Name Server
*   **CN** – Canonical Name

Edit the zone file.

```
sudo vim /etc/bind/forward.computingforgeeks.local.db
```


Modify it as per your set domain name.

```
$TTL    604800
@       IN      SOA     ns1.computingforgeeks.local. root.ns1.computingforgeeks.local. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
;@      IN      NS      localhost.
;@      IN      A       127.0.0.1
;@      IN      AAAA    ::1

;Name Server Information

@        IN      NS      ns1.computingforgeeks.local.

;IP address of Name Server

ns1     IN      A       192.168.1.12

;Mail Exchanger

computingforgeeks.local.   IN     MX   10   mail.computingforgeeks.local.

;A – Record HostName To Ip Address

www     IN       A      192.168.1.13
mail    IN       A      192.168.1.14

;CNAME record

ftp     IN      CNAME   www.computingforgeeks.local.
```


The Reverse zone lookup file also has acronyms

*   **PTR** – Pointer
*   **SOA** – Start of Authority

Also here, copy the sample reverse zone file in **/etc/bind** called **_reverse.computingforgeeks.local.db_**

```
sudo cp /etc/bind/db.127 /etc/bind/reverse.computingforgeeks.local.db
```


Edit the contents of the file.

```
sudo vim /etc/bind/reverse.computingforgeeks.local.db
```


In the file, replace the domain name and IP accordingly.

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     computingforgeeks.local. root.computingforgeeks.local. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;

;Name Server Information

@       IN      NS     ns1.computingforgeeks.local.
ns1     IN      A       192.168.1.12
;Reverse lookup for Name Server

12      IN      PTR    ns1.computingforgeeks.local.

;PTR Record IP address to HostName

13     IN      PTR    www.computingforgeeks.local.
14     IN      PTR    mail.computingforgeeks.local.
```


Step 4 – Check BIND DNS syntax
------------------------------

Check the syntax of your created config files. Here we use **_named-checkconf_** to check the syntax. The command should return to shell if there is no error

Let’s check the syntax of the forward and reverse zone files created.

1.Forward zone file

```
$ sudo named-checkzone computingforgeeks.local /etc/bind/forward.computingforgeeks.local.db
zone computingforgeeks.local/IN: loaded serial 3
OK
```


2\. Reverse zone file

```
$ sudo named-checkzone 1.168.192.in-addr.arpa /etc/bind/reverse.computingforgeeks.local.db
zone 1.168.192.in-addr.arpa/IN: loaded serial 3
OK
```


Note that, the serial output from the two checks should be the same, otherwise edit the configurations.

Restart and enable the BIND DNS server.

```
sudo systemctl restart bind9
sudo systemctl enable bind9
```


Check the status of the service.

```
$ systemctl status bind9
 bind9.service - BIND Domain Name Server
     Loaded: loaded (/lib/systemd/system/named.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2021-08-18 11:29:50 EDT; 7s ago
       Docs: man:named(8)
   Main PID: 10575 (named)
      Tasks: 5 (limit: 4928)
     Memory: 26.0M
        CPU: 73ms
     CGroup: /system.slice/named.service
             └─10575 /usr/sbin/named -f -u bind

Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './DNSKEY/IN': 2001:500:12::d0d#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './NS/IN': 2001:500:12::d0d#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './DNSKEY/IN': 2001:7fd::1#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './NS/IN': 2001:7fd::1#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './DNSKEY/IN': 2001:503:c27::2:30#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './NS/IN': 2001:503:c27::2:30#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './DNSKEY/IN': 2001:500:200::b#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: network unreachable resolving './NS/IN': 2001:500:200::b#53
Aug 18 11:29:50 computingforgeeks.local named[10575]: managed-keys-zone: Key 20326 for zone . is now trusted (acceptance timer complete)
Aug 18 11:29:51 computingforgeeks.local named[10575]: resolver priming query complete
```


Step 5 – Test Bind DNS Server
-----------------------------

Go to any client machine, add your new DNS server IP Address in **/etc/resolv.conf** file. In this case, my IP Address is 192.168.1.12

```
sudo vim /etc/resolv.conf
```


In the file, add Bind DNS server IP address

```
nameserver 192.168.1.12
```


Save and exit. Then proceed as below.

There are two options to use here to verify the DNS server i.e **nslookup** or **dig** command.

Using the dig command, verify the forward lookup.

```
dig www.computingforgeeks.local
```


In case you get the output: `command not found`, you will have to install `bind-utils` on EL based systems and `dnsutils` on Debian/Ubuntu systems.

Sample Output for the above command.

```
; <<>> DiG 9.16.1-Ubuntu <<>> www.computingforgeeks.local
;; global options: +cmd
;; Got answer:
;; WARNING: .local is reserved for Multicast DNS
;; You are currently testing what happens when an mDNS query is leaked to DNS
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41776
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
; COOKIE: e3ed02461aea46d2a51e65556120c239169ed7251d0fb2df (good)
;; QUESTION SECTION:
;www.computingforgeeks.local.	IN	A

;; ANSWER SECTION:
www.computingforgeeks.local. 604800 IN	A	192.168.1.13

;; AUTHORITY SECTION:
computingforgeeks.local. 604800	IN	NS	ns1.computingforgeeks.local.
```


From the above output, the answer for **www.computingforgeeks.local** is _**192.168.1.13**_

Confirm the reverse lookup:

```
dig -x 192.168.1.13
```


Sample output:

```
; <<>> DiG 9.16.1-Ubuntu <<>> -x 192.168.1.13
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21058
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
; COOKIE: 1a52341ddbcff799a7011a806120c29ef2fb075582d0e96d (good)
;; QUESTION SECTION:
;13.1.168.192.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
13.1.168.192.in-addr.arpa. 604800 IN	PTR	www.computingforgeeks.local.

;; AUTHORITY SECTION:
1.168.192.in-addr.arpa.	604800	IN	NS	ns1.computingforgeeks.local.

;; ADDITIONAL SECTION:
ns1.computingforgeeks.local. 604800 IN	A	192.168.1.12

;; Query time: 0 msec
;; SERVER: 192.168.1.12#53(192.168.1.12)
;; WHEN: Sat Aug 21 12:08:46 EAT 2021
;; MSG SIZE  rcvd: 157
```


The DNS server’s answer for the reverse lookup 192.168.1.13 is **www.computingforgeeks.local**, for 192.168.1.14 is **mail.computingforgeeks.local** and for 192.168.1.12 is **ns1.computingforgeeks.local**

From the output result, we affirm that the forward and reverse zone lookups are working fine.

Step 6 – Bind Slave DNS Sever setup
-----------------------------------

Your next reading could be how to configure Bind Slave DNS Server on Debian:

*   [Configure Slave BIND DNS Server on Debian](https://computingforgeeks.com/configure-slave-bind-dns-server-on-debian/)

Conclusion
----------

In the above guide, we have triumphantly configured a Master BIND DNS Server on Debian 11 / Debian 10. This is useful to system admins in case they have applications that communicate over the domain names this helps do away with the wearisome task of having to configure your applications on IP changes. I hope this guide was significant.

See more articles on our page.

*   [How To Configure Slave BIND DNS Server on Ubuntu](https://computingforgeeks.com/configure-slave-bind-dns-server-on-ubuntu/)
*   [Configure Master / Slave BIND DNS Server on CentOS 8 / RHEL 8](https://computingforgeeks.com/configure-authoritative-bind-dns-server-on-centos-rhel/)
*   [Install and Use Guacamole Remote Desktop on Debian](https://computingforgeeks.com/install-and-use-guacamole-remote-desktop-on-debian/)