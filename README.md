# GRE Tunnel Setup Script

This project contains a simple script for setting up a GRE (Generic Routing Encapsulation) tunnel between a **DDoS protection server** and a **main server**.

A GRE tunnel is used to securely forward traffic from a subnet through the DDoS protection server before it reaches the main server. This setup provides additional protection against DDoS attacks by ensuring that malicious traffic is filtered before reaching the main server.

---

## How It Works

1. The **DDoS protection server** handles incoming traffic and forwards it through the GRE tunnel.
2. The **main server** receives the filtered traffic from the GRE tunnel.
3. Outgoing traffic from the main server is routed back through the GRE tunnel to the DDoS protection server.

This bidirectional tunneling ensures that the main server remains protected while maintaining proper routing of traffic.

---

## Variable Explanation

| Variable                          | Description                                            |
|-----------------------------------|--------------------------------------------------------|
| `[Hoofdserver_IP]`                | Public IP address of the **main server**               |
| `[DDoS_server_IP]`                | Public IP address of the **DDoS protection server**    |
| `[Tunnel_IP_voor_DDoS_server/30]` | IP address assigned to the GRE tunnel on **DDoS server** side |
| `[Tunnel_IP_voor_Hoofdserver/30]` | IP address assigned to the GRE tunnel on **main server** side |
| `[subnet_IP]`                     | Subnet for which traffic is routed through the GRE tunnel |

> **Note:** Variable names are in Dutch because this script was originally written for a previous project.

---

## Useful Commands

### Removing the GRE Tunnel
To remove the GRE tunnel, use the following command:
```bash
sudo ip tunnel del gre0
```

### Viewing Routes
To view the current routing table:
```bash
ip route show
```

---

## Disclaimer
I am not responsible for the usage of this script. This script was written for a small-scale project, and you should carefully adjust the IP addresses and subnets to match your specific network configuration.

**Incorrect configuration may result in network issues or server inaccessibility.**
