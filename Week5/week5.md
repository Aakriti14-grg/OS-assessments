🌐 Week 5: Network Configuration Fundamentals

Phase 5 – Network Configuration, Performance, and Communication Models

This week focuses on understanding how networks are configured, how data moves across networks, and how system performance is influenced by network design. The concepts discussed form the foundation for secure, efficient, and scalable system communication.

1️⃣ Network Configuration Overview

Network configuration is the process of defining how devices connect, communicate, and securely exchange data within a network. It includes IP addressing, routing, DNS resolution, and the configuration of network interfaces to ensure reliable connectivity.

Key objectives of network configuration include:

Enabling device-to-device communication

Ensuring efficient data delivery

Securing access to network resources

2️⃣ Network Layered Architecture

Modern networks use layered architectures to manage complexity and improve interoperability.

Why Layering Matters

Layered models provide:

Abstraction – hides lower-level complexity

Modularity – changes in one layer do not affect others

Standardisation – enables vendor interoperability

Simplified troubleshooting – faults can be isolated to specific layers

OSI Model Overview

| Layer | Name         | Function                     | Example         |
| ----- | ------------ | ---------------------------- | --------------- |
| 7     | Application  | End-user network services    | HTTP, FTP, SMTP |
| 6     | Presentation | Data formatting & encryption | JPEG, ASCII     |
| 5     | Session      | Session management           | NetBIOS         |
| 4     | Transport    | Reliable data transfer       | TCP, UDP        |
| 3     | Network      | Logical addressing & routing | IP, ICMP        |
| 2     | Data Link    | Physical addressing          | Ethernet, Wi-Fi |
| 1     | Physical     | Hardware transmission        | Cables, voltage |

The OSI model simplifies network design and troubleshooting by separating responsibilities across layers.

3️⃣ IP Addressing and Subnetting

An IP address uniquely identifies a device on a network and enables routing of data between hosts.

Public vs Private IP Addresses

| Type       | Description          | Examples                   |
| ---------- | -------------------- | -------------------------- |
| Public IP  | Globally routable    | Web servers                |
| Private IP | Internal network use | 192.168.0.0/16, 10.0.0.0/8 |

Private IP addressing improves security by isolating internal systems from direct internet exposure.

IPv4 vs IPv6 Comparison

| Feature       | IPv4           | IPv6           |
| ------------- | -------------- | -------------- |
| Address size  | 32-bit         | 128-bit        |
| Address space | ~4.3 billion   | Vastly larger  |
| Notation      | Decimal        | Hexadecimal    |
| Security      | Optional IPSec | Built-in IPSec |

IPv6 addresses the scalability and security limitations of IPv4.

4️⃣ Network Performance Metrics

Network performance directly impacts system responsiveness and user experience.

Key Metrics

| Metric      | Description                        |
| ----------- | ---------------------------------- |
| Bandwidth   | Maximum data transfer rate         |
| Latency     | Time for data to travel end-to-end |
| Jitter      | Variation in packet delay          |
| Packet Loss | Percentage of lost packets         |

Low latency and minimal packet loss are critical for real-time applications.

Diagnostic Tools
| Tool             | Purpose                             |
| ---------------- | ----------------------------------- |
| `ping`           | Measures latency and connectivity   |
| `traceroute`     | Identifies routing paths and delays |
| `ss` / `netstat` | Displays active connections         |

These tools support performance monitoring and troubleshooting.

5️⃣ Network Services and System Integration

Core network services work together to ensure seamless communication.

| Service        | Role                                  |
| -------------- | ------------------------------------- |
| DHCP           | Automatically assigns IP addresses    |
| DNS            | Resolves domain names to IP addresses |
| Firewalls      | Filter and control network traffic    |
| Load Balancers | Distribute traffic across servers     |

When accessing a website:

Device obtains IP via DHCP

Firewall inspects traffic

DNS resolves domain name

Requests are routed to servers

This integration ensures performance, reliability, and security.

6️⃣ Service Discovery

Service discovery allows systems to locate services dynamically without hardcoded IP addresses.

| Method           | Description                     |
| ---------------- | ------------------------------- |
| DNS-based        | Uses DNS records                |
| mDNS / Bonjour   | Local network discovery         |
| Service Registry | Central directory (e.g. Consul) |
| Load Balancers   | Stable service endpoints        |

Service discovery is essential in dynamic and microservice-based environments.

7️⃣ Communication Patterns

Different systems communicate using structured patterns.

Common Patterns
| Pattern           | Description                      | Example              |
| ----------------- | -------------------------------- | -------------------- |
| Client-Server     | Client requests, server responds | Web browsing         |
| Peer-to-Peer      | Nodes share resources directly   | BitTorrent           |
| Publish-Subscribe | Subscribers receive events       | MQTT, Kafka          |
| Microservices     | Service-to-service communication | E-commerce platforms |

Choosing the correct pattern improves scalability, resilience, and performance.

Conclusion

Week 5 explored the fundamentals of network configuration, layered architectures, addressing, performance analysis, and communication models. These concepts underpin secure and efficient system design. Understanding how networks are structured, monitored, and integrated enables administrators to build scalable systems while maintaining performance and security.