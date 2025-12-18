System Architecture Diagram 

 

 ![System architecture design](../images/week1/sys-design.png)

 

Distribution Selection Justification 

Chosen Distribution: Ubuntu 22.04 LTS (Jammy Jellyfish) 

I select Ubuntu 22.04 LTS for the Server VM by comparing its fixed release model, package management, and community support against the other major Linux distribution families. 

Comparison of Linux Distribution Families 

 

Feature 

Debian Family (Ubuntu LTS) 

Red Hat Family (REHL, Fedora) 

SuSE Family (Open SuSE, SLES) 

Arch Family (Arch, Manjaro) 

Release Model 

Fixed release (LTS) 

Fixed release 

Mixed (Fixed for SLES, Rolling for Tumbleweed) 

Rolling release 

Package Manager 

APT (Advanced Package Tool) 

DNF/YUM 

Zypper 

Pacman 

Stability vs Newness 

Fixed release provides long-term stability and security updates. 

Enterprise focused means high stability but often older packages. 

Enterprise focus offers high stability (SLES). 

Prioritizes bleeding-edge software and minimalism, which introduces greater instability risk. 

Maintenance  

Low manual overhead due to LTS support and automatic dependency resolution. 

Standard enterprise maintenance. 

Use YaST for simplified system administration. 

High maintenance: The rolling release model requires the user to constantly monitor and manage system updates. 

Example command 

sudo apt install <package>  

sudo dnf install <package> 

sudo zypper install <package> 

sudo pacman –S <package> 

 

Justification for Choosing Ubuntu 22.04 LTS 

I think the choice of Ubuntu 22.04 LTS is the most appropriate for a robust, long-term server environment due to the following reasons, directly addressing modern OS challenges. 

LTS for stability and Security: A fixed-release, Long-Term Support (LTS) system ensures a predictable and stable platform for the lifespan of the project. This is a core requirement for a server, mitigating the security and system breakage risks inherent in the continuous, Rolling Release model of Arch Linux. 

Resource Management and Sustainability: Ubuntu, like Linux generally, utilizes a Monolithic Kernel architecture which provides the necessary performance for efficient Resource Management (CPU, Memory, I/O), directly contributing to Energy Efficiency and Sustainability. 

Community and Documentation: Ubuntu's widespread adoption means there is a vast pool of documentation and community support, which is critical for easier setup and troubleshooting compared to the more focused Red Hat or SUSE enterprise communities. 

Workstation Consistency: Selecting Ubuntu for both the Server and Workstation VMs simplifies administration by ensuring both systems use the same APT package management system and command-line tools for tasks like memory monitoring (top, free, htop). 

 

 

Workstation Configuration Decision 

Operating System Choice: Ubuntu (64-bit) 

The choice of the Ubuntu distribution for the Workstation VM is a strategic decision that aligns with several key OS and Linux foundation principles: 

Distribution Family Consistency: Ubuntu belongs to the Debian Family, which uses the APT (Advanced Package Tool). Using a single family for both the Server and Workstation simplifies maintenance by relying on a uniform package management system. 

Access to Command-Line Tools: The Workstation acts as the client, requiring a robust shell environment. Ubuntu natively provides the essential GNU command-line utilities (like bash, ls, grep), which are necessary for tasks like system navigation (ls, cd, pwd) and file operations (cp, mv, rm). 

Operating System Architecture: Like other modern Linux distributions, Ubuntu utilizes a Hybrid Kernel architecture (or sometimes classified as Monolithic), offering good performance and improved security through modularity and a well-defined System Call Interface between User Space and Kernel Space. 

 

Resource Allocation Justification 

The allocation of resources balances performance requirements with the principle of efficient resource utilization. 

Base Memory (2048 MB RAM): 

Allocation (2048 MB RAM per VM): Both the Server and Workstation have been assigned 2048 MB of base memory to ensure a stable operating environment. 

Performance Optimization: This allocation is intended to provide enough physical RAM to the Guest OS to minimize the need for Virtual Memory (swapping), which is significantly slower than physical RAM and can lead to performance degradation. 

Energy Efficiency: By optimizing the RAM to 2GB, the system reduces unnecessary energy consumption on the host machine while still providing sufficient "headroom" for OS processes. 

 

 

Processors (4 vCPUs): 

Allocation (4 vCPUs per VM): Each VM is configured with 4 virtual CPUs to support modern computing requirements. 

Parallel Execution: Allocating multiple processors enables Multi-threading and parallel execution, which directly improves CPU Utilization and system responsiveness. 

Bottleneck Prevention: This configuration ensures that neither the Workstation nor the Server encounters a CPU Bottleneck, where the processor cannot handle the task load, resulting in system lag. 

 

 

Storage and File System Management 

Workstation (50GB) / Server (25GB): Storage is allocated based on anticipated file use, ensuring sufficient space for the File System and preventing disk-related failures. 

 

 

Networking and Isolation (Host-Only Adapter) 

The configuration of the Workstation using a Host-Only adapter promotes resource isolation: 

Host-Only Network: Both VMs utilize a Host-Only Adapter to create a private network segment (192.168.56.0/24). 

Security Enforcement: This setup provides Resource Isolation, protecting the experimental lab environment from external internet threats while allowing internal communication between the systems. 

 

 

Network Configuration Documentation 

This documentation covers the VirtualBox networking settings and the resulting IP addressing scheme for the isolated lab environment. 

 

VirtualBox Settings and Resource Isolation 

The virtual environment utilizes the Host-Only Adapter setting (Adapter 1: 'VirtualBox Host-Only Ethernet Adapter') for connecting the Server VM and the Workstation VM. 

Isolation Mechanism: The Host-Only Adapter creates a private network that is isolated from the external physical network, ensuring that the Virtual Machines cannot communicate with the outside world. This configuration is critical for Resource Isolation, preventing applications from interfering with others. 

Networking Layer: The Operating System (OS) manages the virtual Network Interfaces within this isolated environment, a core function of the OS's Resource Management. 

 

IP Addressing Documentation 

The specific IP addressing gathered using the ip addr command provides the necessary details for reliable inter-VM and Host-to-VM communication: 

System 

Role 

IP Address (from ip addr) 

Subnet Mask (/24) 

Interface Name 

Server VM 

Host for services 

192.168.56.10 

255.255.255.0 

enp0s3 

Workstation VM 

Client/Administration 

192.168.56.11 

255.255.255.0 

enp0s3 

 

 

 

Using a CLI, document system specification 

The following specifications were gathered from the running VMs using the requested Command-Line Utilities. These tools are essential for monitoring system resources and retrieving foundational system information. 

 

Server VM (Ubuntu 22.04 LTS) 

 

 

Command 

Output Summary 

Relevance to System Architecture 

-a 

Linux server01 6.8.0-71 ......x86_64 GNU/Linux  

Documents the Kernel Information. The kernel is the core component responsible for Resource Management (CPU, memory, I/O). 

lsb_release –a  

Distributor ID: Ubuntu ... 

Release: 24.04 LTS 

Codename: noble 

Confirms the use of a Debian Family distribution with a stable Fixed Release (LTS) model. 

free -h 

total: 3.8G used: 397M free: 3.4G buff/cache: 210M 

 

Shows Physical and Swap Memory Overview. The large amount of free memory suggests that the 4096 MB allocation is efficient, minimizing reliance on slower Virtual Memory. 

df -h 

/dev/mapper/...-lv 12G 4.8G 5.9G 45% / 

Shows the available File System storage and usage. The OS handles all data organization and retrieval on storage devices. 

ip addr 

inet 192.168.56.10/24 ... enp0s3 

Confirms the network interface and IP address, which is critical for Resource Isolation and uname communication within the Host-Only Network. 

 

Workstation VM (Ubuntu 24.04 LTS) 

 

 

Command 

Output Summary 

Relevance to System Architecture 

uname -a 

Linux workstation-vm 6.14.8-27-generic ... x86_64 GNU/Linux 

Confirms the underlying OS is a GNU/Linux system and provides the kernel version used for managing hardware resources. 

lsb_release -a 

Distributor ID: Ubuntu Release: 24.04 LTS Codename: noble 

Confirms that the Workstation uses the same APT package management family as the Server, simplifying maintenance 

free -h 

total: 3.8G used: 1.0G free: 2.2G buff/cache: 853M 

Documents memory usage. The higher usage compared to the server is expected for a workstation (client) and helps monitor resource consumption to prevent Memory Bottlenecks. 

df -h 

/dev/sda2 49G 5.1G 42G 11% / 

Documents disk usage, confirming the larger 50GB storage allocation is available. 

ip addr 

inet 192.168.56.11/24 ... enp0s3 

Confirms the network address, enabling communication with the Server VM (192.168.56.10) across the isolated network. 

 