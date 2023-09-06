**Scenario:**
Imagine you have a small office network with several computers, and you want to set up DHCP to automatically assign IP addresses to these computers when they connect to the network.

**Example IP Address Allocation with DHCP:**

1. **DHCP Server Setup:**
   - You set up a DHCP server on your network. This server will be responsible for allocating IP addresses to the client computers.

2. **Client Request:**
   - A computer (let's call it "Computer A") joins the network and wants to obtain an IP address so that it can communicate with other devices on the network.

3. **DHCP Discovery:**
   - Computer A broadcasts a DHCP discovery message on the network to find a DHCP server. This message essentially says, "I need an IP address, and I'm looking for a DHCP server."

4. **DHCP Server Response:**
   - The DHCP server receives the discovery message from Computer A and responds with an offer. In the offer, the DHCP server suggests an available IP address that Computer A can use.

5. **IP Address Assignment:**
   - Computer A accepts the offered IP address from the DHCP server. The DHCP server then reserves this IP address for Computer A's use for a specified lease duration (e.g., 24 hours).

6. **Configuration Details:**
   - Along with the IP address, the DHCP server provides additional network configuration details to Computer A, such as the subnet mask, default gateway (router) address, DNS server addresses, and more.

7. **Configuration Application:**
   - Computer A configures its network settings with the provided IP address and configuration details. Now, Computer A can communicate on the network using its newly assigned IP address.

8. **Lease Duration:**
   - The IP address assigned to Computer A has a lease duration, which means it's valid for a specific period (e.g., 24 hours). Before the lease expires, Computer A can request a renewal from the DHCP server. If the lease expires, the DHCP server can reassign the IP address to another device.

**Example IP Address Assignment:**
Let's say the DHCP server assigns the following IP address to Computer A:

- IP Address: 192.168.1.100
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.1.1 (router's address)
- DNS Servers: 8.8.8.8 and 8.8.4.4 (Google's public DNS servers)

Now, Computer A is configured with the IP address 192.168.1.100 and can communicate with other devices on the network using this address. DHCP simplifies the process of IP address assignment, making it easier to manage and maintain IP resources in a network.
