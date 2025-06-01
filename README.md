# *Windows Firewall Configuration Documentation*

## *Objective*
This repository documents the process of configuring and testing basic firewall rules on Windows using Windows Firewall. 
The goal was to block inbound traffic on a specific port and verify the effectiveness of the firewall rules.

## *Tools Used*
- Windows Firewall (Windows built-in firewall management tool)
- Command Prompt (for testing connections)

## *Steps Taken*

### 1. Open Windows Firewall Configuration Tool
- Press 'Windows + R', type 'wf.msc', and press 'Enter'.
- This opens the Windows Firewall with Advanced Security management console.

### 2. List Current Firewall Rules
- Click on **Inbound Rules** in the left pane to view existing rules.

### 3. Add a Rule to Block Inbound Traffic on Port 23 (Telnet)
- Click on **New Rule...** in the right pane.
- Select **Port** and click **Next**.
- Choose **TCP** and specify port **23**, then click **Next**.
- Select **Block the connection** and click **Next**.
- Choose when to apply the rule (Domain, Private, Public), then click **Next**.
- Give the rule a name, for example: **Block Telnet**, then click **Finish**.

### 4. Test the Rule
- Open **Command Prompt**.
- Run the command: 
   > telnet localhost 23
- "The connection should fail", >> indicating that traffic on port 23 is properly blocked by the firewall.

### 5. Remove the Test Block Rule
- Go back to **Inbound Rules** in Windows Firewall.
- Find the **Block Telnet** rule.
- Right-click the rule and select **Delete** to remove it and restore original firewall state.

### Summary of How Windows Firewall Filters Traffic
Firewalls, including Windows Firewall, serve as a security barrier between a trusted internal network and untrusted external networks (such as the internet). They filter traffic based on a set of predefined rules, which can be customized according to the user's needs. Here are the key aspects of how Windows Firewall filters traffic:

**1. Rule-Based Filtering:**

Firewalls operate based on rules that specify which types of traffic are allowed or blocked. 
Each rule can define conditions based on various criteria.

**2. Criteria for Filtering:**

- *Source and Destination IP Addresses:* Firewalls can permit or deny traffic based on the IP addresses of the sender and receiver. 
For example, traffic from a specific IP can be blocked while allowing others.

- *Source and Destination Ports:* Rules can specify which ports are open or closed. For instance, blocking port 23 (Telnet) prevents unauthorized access to that service.

- *Protocols:* Firewalls can filter traffic based on the protocol used, such as TCP or UDP. This allows for more granular control over the types of traffic that are allowed.

- *Direction of Traffic:* Rules can be set for inbound (incoming) and outbound (outgoing) traffic, allowing users to control what can enter or leave the network.

**3. Profiles:**
Windows Firewall allows users to create rules based on different network profiles (Domain, Private, Public). 
This means that the same rule can behave differently depending on the network environment, enhancing security.

**4. Application Control:**
Firewalls can also filter traffic based on specific applications or services. 
This means that a firewall can allow or block traffic for a particular program, providing an additional layer of security.

**5. Logging and Alerts:**
Firewalls can log traffic and alert users to suspicious activity. 
This helps in monitoring and responding to potential threats in real-time.
By implementing these filtering mechanisms, Windows Firewall helps protect the system from unauthorized access, malware, and other network-based threats, ensuring a more secure computing environment.
