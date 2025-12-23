⚙️ Week 6: Performance Evaluation and Analysis

Phase 6 – System Performance Measurement and Interpretation

This phase focuses on evaluating system performance under different workloads and interpreting observed behaviour using operating system concepts. Unlike earlier weeks, the emphasis here is not on configuration, but on measurement, analysis, and reasoning about how system resources are utilised.

1️⃣ Performance Evaluation Objectives

The primary objectives of this phase are to:

Assess how system resources respond to workload pressure

Identify potential performance bottlenecks

Interpret observed behaviour using OS concepts such as scheduling, memory management, and I/O handling

Establish a baseline for future optimisation

Performance evaluation enables informed decisions about scalability, reliability, and system tuning.

2️⃣ Test Environment Overview

The performance evaluation is conducted on the previously configured virtualised environment.

| Component      | Description                          |
| -------------- | ------------------------------------ |
| Server VM      | Ubuntu Linux (secure, hardened)      |
| Workstation VM | Ubuntu Linux (remote administration) |
| Network        | Host-Only Adapter                    |
| Access Method  | Secure Shell (SSH)                   |

The system operates in an isolated environment, ensuring that measured performance reflects internal system behaviour rather than external network variability.

3️⃣ Workload Categories Evaluated

Performance evaluation considers multiple workload categories to provide a comprehensive assessment of system behaviour.

| Workload Type     | Description               | Resource Focus          |
| ----------------- | ------------------------- | ----------------------- |
| CPU-intensive     | High computational demand | CPU scheduling          |
| Memory-intensive  | Large memory allocation   | RAM and swap            |
| I/O-intensive     | Frequent disk access      | File system performance |
| Network-intensive | High data transfer        | Network stack           |
| Mixed workload    | Realistic server usage    | Overall system balance  |

This categorisation enables targeted analysis of individual subsystems.

4️⃣ Performance Metrics Analysed

The following metrics are used to evaluate system performance:

| Metric             | Description             | Importance                        |
| ------------------ | ----------------------- | --------------------------------- |
| CPU utilisation    | Percentage of CPU usage | Indicates processing load         |
| Load average       | Runnable process demand | Reflects scheduling pressure      |
| Memory usage       | RAM consumption         | Detects memory pressure           |
| Swap activity      | Use of virtual memory   | Indicates memory exhaustion       |
| Disk I/O wait      | Time waiting on storage | Identifies I/O bottlenecks        |
| Network throughput | Data transfer rate      | Measures communication efficiency |

Together, these metrics provide a holistic view of system performance.

5️⃣ Monitoring and Observation Tools

Performance data is collected using standard Linux monitoring tools.

| Tool      | Purpose                              |
| --------- | ------------------------------------ |
| `htop`    | Real-time CPU and process monitoring |
| `free -h` | Memory and swap analysis             |
| `vmstat`  | Memory, process, and I/O statistics  |
| `iostat`  | Disk I/O performance                 |
| `ss`      | Network socket monitoring            |

These tools enable both real-time observation and trend analysis.

6️⃣ Observed Performance Behaviour (Conceptual Analysis)
CPU Behaviour

Under CPU-intensive workloads, CPU utilisation increases significantly, while load average reflects the number of runnable processes competing for CPU time. Linux’s scheduler distributes CPU time fairly, preventing starvation.

Memory Behaviour

Memory-intensive workloads result in increased RAM usage. If physical memory becomes constrained, swap usage may increase, leading to performance degradation due to slower disk access.

Disk I/O Behaviour

I/O-intensive workloads increase disk wait time (iowait). High I/O wait indicates that processes are blocked while waiting for storage operations to complete.

Network Behaviour

Network-intensive workloads increase throughput but may also introduce latency if bandwidth limits are reached. Efficient buffering and TCP congestion control help stabilise communication.

7️⃣ Bottleneck Identification

Based on performance principles, potential bottlenecks include:

| Bottleneck      | Cause                        | Impact               |
| --------------- | ---------------------------- | -------------------- |
| CPU saturation  | Excessive parallel processes | Slower response time |
| Memory pressure | Insufficient RAM             | Increased swap usage |
| Disk contention | High I/O demand              | Process blocking     |
| Network limits  | Bandwidth constraints        | Increased latency    |

Identifying these bottlenecks enables targeted optimisation strategies.

8️⃣ Performance vs Security Trade-Offs

Security controls can influence system performance.

| Security Control         | Performance Impact | Justification            |
| ------------------------ | ------------------ | ------------------------ |
| Firewall rules           | Minimal overhead   | Improved access control  |
| SSH encryption           | Slight CPU usage   | Secure communication     |
| Mandatory Access Control | Minor latency      | Strong process isolation |

These trade-offs are acceptable, as security benefits outweigh the marginal performance cost.

Conclusion

Week 6 demonstrated how system performance can be evaluated and interpreted using operating system principles. By analysing CPU, memory, disk, and network behaviour under varying workloads, it is possible to identify bottlenecks and understand resource interactions. This evaluation establishes a foundation for informed optimisation while maintaining security and system stability.

