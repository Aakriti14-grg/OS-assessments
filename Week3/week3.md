📘 Week 3: Application Selection for Performance Testing

Phase 3 – Performance Evaluation Preparation


1️⃣ Application Selection Matrix

The following applications were selected to represent different workload types. Each application stresses a specific system resource, enabling meaningful performance evaluation across CPU, memory, disk I/O, network, and server workloads.
| Workload Type      | Application      | Purpose                     | Justification                                                                        |
| ------------------ | ---------------- | --------------------------- | ------------------------------------------------------------------------------------ |
| CPU-Intensive      | `stress-ng`      | CPU stress testing          | Generates controlled CPU load to evaluate scheduling efficiency and CPU utilisation  |
| RAM-Intensive      | `stress-ng` (vm) | Memory stress testing       | Allocates and frees memory aggressively to test RAM pressure and swapping behaviour  |
| I/O-Intensive      | `fio`            | Disk I/O benchmarking       | Simulates real-world read/write workloads and measures throughput, latency, and IOPS |
| Network-Intensive  | `iperf3`         | Network performance testing | Measures bandwidth, packet loss, and network throughput between VMs                  |
| Server Application | `nginx`          | Lightweight web server      | Represents a real server workload handling concurrent client requests                |

These applications collectively cover CPU, Memory, Storage, Network, and Server-side workloads, providing a balanced and realistic performance testing environment.


2️⃣ Installation Documentation (SSH-based)

All installations are performed remotely via SSH from the Workstation VM to the Server VM, simulating real-world system administration.

ssh aakriti@192.168.56.10

Install CPU & Memory Stress Tool
sudo apt update
sudo apt install stress-ng -y

Install Disk I/O Benchmark Tool
sudo apt install fio -y

Install Network Performance Tool
sudo apt install iperf3 -y

Install Server Application (Nginx)
sudo apt install nginx -y


3️⃣ Expected Resource Profiles

This section documents the anticipated system behaviour for each workload before testing begins.
| Application          | CPU Usage | Memory Usage | Disk I/O  | Network   | Expected Behaviour                          |
| -------------------- | --------- | ------------ | --------- | --------- | ------------------------------------------- |
| `stress-ng` (CPU)    | Very High | Low          | Minimal   | None      | CPU cores reach near-100% utilisation       |
| `stress-ng` (Memory) | Medium    | Very High    | Low       | None      | Increased RAM usage, possible swap activity |
| `fio`                | Medium    | Low          | Very High | None      | High disk throughput and IOPS               |
| `iperf3`             | Low       | Low          | None      | Very High | Network bandwidth saturation                |
| `nginx`              | Medium    | Medium       | Low       | Medium    | Stable multi-request handling               |


4️⃣ Monitoring Strategy

Each application is monitored using resource-specific tools to accurately measure performance impact.

CPU & Memory Monitoring
htop
free -h

Tracks CPU utilisation, process scheduling, and memory consumption
Identifies CPU bottlenecks and memory pressure


Disk I/O Monitoring
iostat -xz 1
vmstat 1

Measures disk throughput, I/O wait time, and queue depth
Identifies storage bottlenecks


Network Monitoring
iperf3 -s   # Server
iperf3 -c 192.168.56.10   # Client

Measures bandwidth, jitter, and packet loss

Server Monitoring
systemctl status nginx
curl http://localhost

Verifies service availability and responsiveness


5️⃣ Performance Testing Rationale

This testing approach follows operating system performance principles:

CPU Scheduling → stress-ng validates fair scheduling and utilisation

Memory Management → memory stress tests observe swap and caching

File System Performance → fio evaluates I/O latency and throughput

Network Stack Efficiency → iperf3 validates bandwidth handling

Real-World Server Load → nginx represents production-like services

This ensures holistic system evaluation, aligning with OS resource management concepts.