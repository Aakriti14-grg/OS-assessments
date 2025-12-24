## 🧪 Week 3: Application Selection for Performance Testing

## Phase 3: Performance Testing Tool Selection and Justification

This journal entry documents the selection of appropriate applications and benchmarking tools for evaluating system performance in later phases of the coursework. The objective of this phase is to identify representative workloads that allow controlled, repeatable, and meaningful performance analysis of CPU, memory, storage, and network subsystems.

## 1️⃣ Purpose of Application Selection

Performance testing requires carefully chosen tools that can:

- Generate predictable and repeatable workloads  
- Isolate specific system resources (CPU, memory, disk, network)  
- Reflect real-world server usage patterns  
- Provide measurable and interpretable results  

Rather than performing testing immediately, this phase focuses on planning and justification, ensuring that later measurements are methodologically sound.

## 2️⃣ Workload Categories

To evaluate system performance comprehensively, workloads are categorised based on the primary resource they stress.

| Workload Category    | Target Resource    | Purpose                             |
| -------------------- | ------------------ | ----------------------------------- |
| CPU-intensive        | Processor          | Evaluate scheduling and utilisation |
| Memory-intensive     | RAM & swap         | Observe memory pressure behaviour   |
| I/O-intensive        | Storage            | Measure disk throughput and latency |
| Network-intensive    | Network stack      | Assess bandwidth and connectivity   |
| Application workload | Multiple resources | Simulate real server usage          |

This categorisation ensures balanced system evaluation.

## 3️⃣ Selected Applications and Tools

The following tools were selected based on reliability, industry usage, and suitability for controlled testing.

| Workload Type      | Application      | Purpose                     | Justification                                                                        |
| ------------------ | ---------------- | --------------------------- | ------------------------------------------------------------------------------------ |
| CPU-Intensive      | `stress-ng`      | CPU stress testing          | Generates controlled CPU load to evaluate scheduling efficiency and CPU utilisation  |
| RAM-Intensive      | `stress-ng` (vm) | Memory stress testing       | Allocates and frees memory aggressively to test RAM pressure and swapping behaviour  |
| I/O-Intensive      | `fio`            | Disk I/O benchmarking       | Simulates real-world read/write workloads and measures throughput, latency, and IOPS |
| Network-Intensive  | `iperf3`         | Network performance testing | Measures bandwidth, packet loss, and network throughput between virtual machines     |
| Server Application | `nginx`          | Lightweight web server      | Represents a realistic server workload handling concurrent client requests           |

These tools collectively allow focused testing of individual subsystems as well as integrated system behaviour.

## 4️⃣ Justification for Tool Selection

**CPU and Memory Testing**

`stress-ng` was selected due to its fine-grained workload control and ability to target specific system components. It enables reproducible CPU and memory stress scenarios while maintaining predictable execution.

**Storage Performance Testing**

`fio` is widely used for storage benchmarking and allows flexible configuration of read/write patterns, block sizes, and concurrency levels, making it suitable for realistic disk performance evaluation.

**Network Performance Testing**

`iperf3` provides accurate measurement of network throughput and is commonly used in enterprise environments. It allows direct performance testing between the Server and Workstation virtual machines.

**Application-Level Testing**

`nginx` was selected as a lightweight and widely deployed web server. It represents a realistic server workload that combines CPU usage, memory allocation, disk access, and network communication.

## 5️⃣ Testing Scope and Methodology Alignment

At this stage, no performance testing is executed. The focus remains on:

- Tool selection and justification  
- Alignment with performance metrics defined in Week 2  
- Preparation for controlled execution in Weeks 6 and 7  

This separation between planning and execution ensures clarity, reproducibility, and academic rigour.

## Conclusion

Week 3 established a structured and justified selection of applications and benchmarking tools for performance evaluation. By categorising workloads and choosing industry-relevant tools, the system is prepared for controlled performance measurement and optimisation in subsequent weeks. This planning phase ensures that later performance results are meaningful, comparable, and analytically valid.
