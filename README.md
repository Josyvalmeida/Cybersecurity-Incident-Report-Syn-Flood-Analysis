# Project: Cybersecurity Incident Report - SYN Flood Analysis

## 1. Executive Summary
This project consists of an analysis of a network intrusion incident involving a travel agency's web server. As a security analyst, I identified the root cause of service disruptions and documented the technical impact on network performance.

## 2. Incident Identification
* **Attack Type:** TCP SYN Flood (Denial of Service).
* **Symptoms:** Connection timeout error messages for users and employees.
* **Evidence:** Packet sniffing revealed an abnormally large number of SYN requests originating from a single, unfamiliar IP address.

## 3. Technical Analysis (The TCP Three-Way Handshake)
To understand how this attack disrupts the network, we must look at the standard TCP connection process:

1.  **SYN (Synchronize):** The client sends a request to open a connection.
2.  **SYN-ACK (Synchronize-Acknowledge):** The server acknowledges the request and reserves resources for the client.
3.  **ACK (Acknowledge):** The client sends a final confirmation to establish the connection.

### How the SYN Flood Impacts Performance
* **Malicious Action:** In this scenario, the attacker sends a massive volume of SYN packets but never sends the final ACK packet.
* **Resource Exhaustion:** The server is forced to keep "half-open" connections active, waiting for acknowledgments that never arrive.
* **Service Malfunction:** Because the server's connection capacity is exhausted by these fake requests, it loses the ability to respond to legitimate traffic from customers and employees, leading to the observed "connection timeout".

## 4. Response and Mitigation
* **Immediate Mitigation:** The server was taken offline temporarily to recover its operating status.
* **Firewall Configuration:** The firewall was configured to block the specific IP address associated with the attack.
* **Post-Incident Note:** While IP blocking was effective, it is a temporary solution as attackers can spoof other IP addresses to bypass blocks.

---
*This analysis was completed as part of a professional cybersecurity certification exercise.*

