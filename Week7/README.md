## 🚀 Week 7: Performance Optimisation and System Tuning

## Phase 7 – Performance Optimisation Based on Measured Behaviour

This phase focuses on applying performance optimisation strategies based on the system behaviour analysed in Week 6. Rather than making arbitrary changes, optimisation decisions are guided by observed performance characteristics and operating system principles.

---

## 1️⃣ Optimisation Objectives

The objectives of this phase are to:
- Improve system responsiveness under load  
- Reduce resource contention and bottlenecks  
- Maintain system stability and security  
- Apply targeted tuning rather than over-optimisation  

Performance optimisation aims to achieve efficient resource utilisation while preserving reliability.

---

## 2️⃣ Optimisation Strategy Overview

Optimisation strategies are applied across multiple system layers.

| Layer    | Optimisation Focus              |
|----------|--------------------------------|
| CPU      | Scheduling efficiency           |
| Memory   | Reduced pressure and swap usage |
| Storage  | Improved I/O handling           |
| Network  | Reduced latency and congestion  |
| Services | Efficient background processing |

This layered approach aligns with the principle of **defence-in-depth**, applied to performance rather than security.

---

## 3️⃣ CPU Optimisation Strategies

### Process Scheduling and Load Control

Excessive parallel workloads can lead to CPU saturation. Optimisation focuses on controlling load rather than maximising throughput at all times.

| Technique       | Description                | Benefit                                         |
|-----------------|----------------------------|-------------------------------------------------|
| Nice values     | Adjust process priority    | Prevents low-priority tasks from dominating CPU |
| Load monitoring | Observe load average       | Avoids oversubscription                         |
| Service tuning  | Limit unnecessary services | Frees CPU cycles                                |

Linux’s Completely Fair Scheduler (CFS) ensures fairness, but tuning process priorities improves responsiveness for critical tasks.

---

## 4️⃣ Memory Optimisation Strategies

### Reducing Memory Pressure

Memory pressure can significantly degrade performance due to swap usage.

| Technique            | Description                | Benefit                |
|----------------------|----------------------------|------------------------|
| Swappiness tuning    | Reduce aggressive swapping | Improves response time |
| Cache utilisation    | Leverage page cache        | Faster data access     |
| Service optimisation | Reduce memory footprint    | Prevents swap activity |

Optimising memory usage reduces reliance on slower disk-based swap space.

---

## 5️⃣ Storage and File System Optimisation

### I/O Efficiency Improvements

Disk I/O performance is critical for application responsiveness.

| Technique                    | Description               | Benefit              |
|------------------------------|---------------------------|----------------------|
| I/O scheduler selection      | Optimise request ordering | Reduced latency      |
| Log rotation                 | Prevent large log files   | Improved disk access |
| Temporary storage management | Clean unused files        | Frees disk space     |

Reducing unnecessary disk access minimises I/O wait and improves throughput.

---

## 6️⃣ Network Performance Optimisation

### Network Efficiency

Network optimisation focuses on preventing congestion and latency.

| Technique                  | Description               | Benefit                          |
|----------------------------|---------------------------|----------------------------------|
| Firewall rule optimisation | Reduce unnecessary checks | Lower packet processing overhead |
| Connection reuse           | Persistent connections    | Reduced handshake overhead       |
| Service isolation          | Limit exposed services    | Improved stability               |

Efficient network configuration improves both performance and security.

---

## 7️⃣ Security–Performance Balance

Optimisation must not compromise security.

| Security Control         | Performance Consideration | Decision |
|--------------------------|---------------------------|----------|
| SSH encryption           | Minor CPU overhead        | Retained |
| Firewall filtering       | Minimal latency           | Retained |
| Mandatory Access Control | Slight overhead           | Retained |

Security controls remain enabled, as their performance impact is negligible compared to the risk reduction they provide.

---

## 8️⃣ Evaluation of Optimisation Impact

The effectiveness of optimisation is evaluated by comparing system behaviour before and after tuning.

| Metric                | Expected Outcome        |
|-----------------------|-------------------------|
| CPU utilisation       | More stable under load  |
| Load average          | Reduced sustained peaks |
| Memory usage          | Lower swap activity     |
| Disk I/O wait         | Reduced blocking time   |
| System responsiveness | Improved consistency    |

These improvements demonstrate informed and controlled optimisation.

---

## Conclusion

Week 7 demonstrated how performance optimisation can be applied systematically based on measured system behaviour. By targeting CPU scheduling, memory management, storage efficiency, and network configuration, the system achieves improved performance without compromising security or stability. This phase completes the transition from system analysis to practical optimisation.
