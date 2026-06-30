# Lab: VirtualBox Network Architecture

## Objective
To design and implement an isolated virtual network environment that allows for controlled communication between a Domain Controller and client workstations while maintaining separation from the host machine's physical network.

## Technical Environment
* **Platform:** Oracle VM VirtualBox
* **Hypervisor Network Modes:** Internal Network / NAT
* **Goal:** Create a private sandbox for Active Directory and domain-based testing.

## Lab Workflow: Step-by-Step

### 1. Initial VM Provisioning
* Created separate Virtual Machines for the Windows Server (Domain Controller) and the Windows 11 client.
* Standardized resource allocation (CPU/RAM/Disk) to ensure consistent performance during lab testing.
<img width="1766" height="991" alt="VirtualBox Manager" src="https://github.com/user-attachments/assets/4c626107-a95e-46ec-a5c2-01787b60b7e2" />

### 2. Network Adapter Configuration
* **Internal Network Mode:** Set both VMs to "Internal Network" mode. This creates an isolated virtual switch that is invisible to the external network, ensuring the safety of the host machine.
* **NAT (Optional/Secondary):** Configured a secondary adapter on the server (NAT) only for initial software updates and driver downloads, then disabled it to maintain strict isolation.
<img width="1561" height="1016" alt="Network Adapter Settings" src="https://github.com/user-attachments/assets/cc99ffaa-4113-4143-b51c-a047a369a173" />
<img width="1502" height="887" alt="Network Adaptor Settings2" src="https://github.com/user-attachments/assets/8056c9fd-cf22-40e2-9640-48af7ecb4909" />


### 3. IP Addressing Strategy
* Assigned static IP addresses to the Domain Controller and client to ensure persistent connectivity.
* Configured the client's DNS settings to point directly to the IP address of the Domain Controller to enable successful domain joining.
* <img width="1887" height="1005" alt="Adding a client to a Domain" src="https://github.com/user-attachments/assets/b8b60049-e05c-4cf2-abd3-069f4982090e" />


### 4. Connectivity Validation
* Used `ping` to test end-to-end communication between the Domain Controller and the client within the internal network.
* Verified NIC (Network Interface Card) binding within the guest OS to ensure both machines were on the same subnet.

## Key Learnings
* **Security & Isolation:** Learned the critical importance of "Internal Network" mode for building labs that do not interfere with—or expose—the host machine to potential vulnerabilities.
* **Troubleshooting:** Gained experience in identifying "black hole" network issues where incorrect DNS settings or adapter configurations prevent VMs from seeing each other.
* **Scalability:** Understood how to architect a lab network that can grow from two VMs to a complex multi-server domain environment.
