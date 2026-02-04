The following table includes common cisco security configuration and management commands

| Category | Configuration Mode | Command Syntax | Purpose |
| :--- | :--- | :--- | :--- |
| **AAA Enablement** | Global Config | `aaa new-model` | Enables **AAA services** and the configuration of method lists. |
| **User Access** | Global Config | `username [name] privilege [level] secret [pwd]` | Creates a local user with a **hashed password** and specific privilege level. |
| **Authentication** | Global Config | `aaa authentication login [list] [method1] [method2]` | Defines how the router prompts for **character mode login** credentials. |
| **Authorization** | Global Config | `aaa authorization exec [list] [methods]` | Determines if an authenticated user is authorized for a **CLI EXEC shell**. |
| **Authorization** | Global Config | `aaa authorization commands [lvl] [list] [meth]` | Restricts which commands can be issued at a specific **privilege level**. |
| **Accounting** | Global Config | `aaa accounting commands [lvl] [list] start-stop [meth]` | Creates an **audit trail** of commands issued by administrators. |
| **TACACS+ Server** | Global Config | `tacacs-server host [ip] key [key]` | Identifies a remote **TACACS+ server** and its shared secret for encryption. |
| **RADIUS Server** | Global Config | `radius server [name]` | Enters sub-configuration mode to define **RADIUS server** attributes. |
| **Remote Access** | Global Config | `ip ssh version 2` | Enables the more secure **SSH Version 2** protocol for management. |
| **HTTP Security** | Global Config | `ip http secure-server` | Enables the **HTTPS server** for secure web-based management. |
| **Logging** | Global Config | `service timestamps log datetime` | Adds **date and time stamps** to syslog messages for event correlation. |
| **NTP Security** | Global Config | `ntp authenticate` | Enables **NTP authentication** to prevent time-tampering via rogue servers. |
| **Device Hardening** | Global Config | `security passwords min-length [n]` | Enforces a **minimum character length** for all new passwords. |
| **File Security** | Global Config | `secure boot-image` | Creates a **secure bootset** to protect the IOS image from deletion. |
| **RBAC** | Global Config | `parser view [name]` | Enters sub-configuration to define a **parser view** for restricted access. |

### **Layer 2 and Connectivity Security Commands**

| Category | Configuration Mode | Command Syntax | Purpose |
| :--- | :--- | :--- | :--- |
| **Port Access** | Interface Config | `switchport mode access` | Administratively locks a port to **access mode** to prevent trunking. |
| **VLAN Hopping** | Interface Config | `switchport nonegotiate` | Disables **Dynamic Trunking Protocol (DTP)** to prevent unauthorized trunking. |
| **STP Security** | Interface Config | `spanning-tree bpduguard enable` | Shuts down a port if it receives **BPDUs**, preventing rogue switches. |
| **STP Security** | Interface Config | `spanning-tree guard root` | Prevents a remote switch from becoming the **Root Bridge** through that port. |
| **MAC Security** | Interface Config | `switchport port-security` | Enables **MAC address filtering** on a specific switch port. |
| **MAC Security** | Interface Config | `switchport port-security maximum [n]` | Limits the number of **learned MAC addresses** on an interface. |
| **MAC Security** | Interface Config | `switchport port-security mac-address sticky` | Saves dynamically learned MACs into the **running configuration**. |
| **DHCP Security** | Global Config | `ip dhcp snooping` | Enables protection against **rogue DHCP servers** globally. |
| **ARP Security** | Global Config | `ip arp inspection vlan [id]` | Enables **Dynamic ARP Inspection (DAI)** for a specific VLAN. |
| **ARP Security** | Interface Config | `ip arp inspection trust` | Configures an interface as **trusted** for ARP traffic (usually for uplinks). |

### **Virtual Private Network (VPN) Commands**

| Category | Configuration Mode | Command Syntax | Purpose |
| :--- | :--- | :--- | :--- |
| **IKEv1 Phase 1** | Global Config | `crypto isakmp policy [priority]` | Defines **encryption, hash, and DH group** for IKEv1 Phase 1. |
| **IKEv1 Key** | Global Config | `crypto isakmp key [key] address [ip]` | Sets the **pre-shared key** for a specific remote IPsec peer. |
| **IKEv2 Enable** | Global Config | `crypto ikev2 enable [interface]` | Activates the **IKEv2 protocol** on a specific physical interface. |
| **IKEv2 Policy** | Global Config | `crypto ikev2 policy [priority]` | Defines the **proposal suite** for IKEv2 security associations. |
| **IPsec Phase 2** | Global Config | `crypto ipsec transform-set [name] [algos]` | Defines the **security algorithms** for the data encryption tunnel. |
| **Crypto Map** | Global Config | `crypto map [name] [n] ipsec-isakmp` | Links the **ACL, peer, and transform-set** to an interface. |
| **Interface Application** | Interface Config | `crypto map [name]` | Applies the **crypto map policy** to a physical interface. |
| **ASA Tunneling** | ASA Global Config | `tunnel-group [ip] type ipsec-l2l` | Creates a **connection profile** for a site-to-site VPN peer. |
| **ASA Group Policy** | ASA Global Config | `group-policy [name] internal` | Defines **user-level attributes** like tunnel protocols and DNS. |
| **Address Pool** | ASA Global Config | `ip local pool [name] [range]` | Defines an **IP range** to assign to remote-access VPN clients. |
| **Tunnel Mode** | Interface Config | `tunnel mode ipsec ipv4` | Sets a **Virtual Tunnel Interface (VTI)** to use native IPsec. |

### **NetFlow and Network Visibility Commands**

| Category | Configuration Mode | Command Syntax | Purpose |
| :--- | :--- | :--- | :--- |
| **NetFlow Feature** | NX-OS Global | `feature netflow` | Enables **NetFlow capabilities** on Nexus-based devices. |
| **Flow Record** | Global Config | `flow record [name]` | Enters configuration mode to define **key/non-key fields**. |
| **Key Fields** | Flow Record Config | `match [ipv4/ipv6/transport/etc]` | Defines the attributes that uniquely identify a **traffic flow**. |
| **Non-Key Fields** | Flow Record Config | `collect [counter/interface/etc]` | Defines **metadata** (like packet counts) to be collected for flows. |
| **Flow Monitor** | Global Config | `flow monitor [name]` | Creates a monitor to associate a **record and exporter**. |
| **Flow Exporter** | Global Config | `flow exporter [name]` | Defines the **destination IP and port** for NetFlow data. |
| **Export Protocol** | Flow Exporter Config| `export-protocol ipfix` | Sets the export format to the **IETF standard IPFIX**. |
| **Interface Binding** | Interface Config | `ip flow monitor [name] input` | Activates **flow monitoring** on an ingress or egress interface. |

### **Control and Data Plane Protection Commands**

| Category | Configuration Mode | Command Syntax | Purpose |
| :--- | :--- | :--- | :--- |
| **CoPP Policy** | Global Config | `policy-map type control subscriber [name]`| Defines a **Control Plane Policing** policy for the CPU. |
| **CoPP Action** | Policy-Map Config | `police [rate] conform-action [act]` | Sets **rate-limiting** for specific control plane traffic types. |
| **CoPP Application** | Control-Plane Config | `service-policy input [name]` | Applies the **CoPP policy** to the aggregate control plane. |
| **OSPF Security** | Interface Config | `ip ospf authentication message-digest` | Enables **MD5 authentication** for OSPF routing updates. |
| **EIGRP Security** | Interface Config | `ip authentication mode eigrp [as] md5` | Enables **MD5 authentication** for EIGRP routing updates. |
| **BGP Security** | Router BGP Config | `neighbor [ip] password [key]` | Sets an **HMAC-MD5 password** for a specific BGP peer. |
| **IPv6 Guard** | Interface Config | `ipv6 destination-guard` | Blocks traffic from **unknown sources** to protect the neighbor cache. |

### **Verification and Operational Mode Commands**

| Command Syntax | Operational Mode | Purpose |
| :--- | :--- | :--- |
| **`show crypto isakmp sa`** | Privileged EXEC | Displays the status of **IKEv1 security associations**. |
| **`show crypto ikev2 sa`** | Privileged EXEC | Displays the status of **IKEv2 security associations**. |
| **`show ip cef`** | Privileged EXEC | Displays the **CEF table** to identify "receive" adjacency traffic. |
| **`show monitor event-trace`** | Privileged EXEC | Accesses **binary event logs** for crypto or PKI troubleshooting. |
| **`debug crypto ikev2`** | Privileged EXEC | Provides **real-time troubleshooting** for IKEv2 negotiations. |
| **`show running-config all sysopt`** | Privileged EXEC | Verifies **global VPN system options**, such as ACL bypass. |
