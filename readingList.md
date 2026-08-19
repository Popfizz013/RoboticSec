# Reading List

Papers mapped to the sections in [topicsOfInterest.md](topicsOfInterest.md).

## Secure Simulation Frameworks & Datasets

**ROS2-Based Simulation Framework for Cyberphysical Security Analysis of UAVs** — Patil, Gunasekaran, Bobba, Abbas (Oregon State), arXiv:2410.03971
The closest match to the attack-injection bullet. ROS 2 + Gazebo, modular by design, with motion planner, controller, communication models, and attack models as first-class swappable components. Caveat: code release could not be confirmed from the abstract page — worth emailing the authors before building on it.
https://arxiv.org/pdf/2410.03971

**A UAV Testbed for Diagnosing Hardware Vulnerabilities: Quantifying Sim-to-Real Discrepancies in PX4 Flight Logs** — Sensors 2026
The most useful paper for the telemetry-logging half of the bullet. Builds a unified data pipeline on the uORB message bus and ULog format across SITL and real flights, then quantifies where sim and hardware diverge. If we extend a simulator with attack injection, this is the paper that tells us whether the results transfer.
https://doi.org/10.3390/s26103188

**MIXED-SENSE: A Mixed Reality Sensor Emulation Framework for Test and Evaluation of UAVs Against False Data Injection Attacks** — arXiv:2407.09342
Sensor emulation at the boundary between sim and real airframe — lets us inject FDI against actual flight hardware without flying into anything.
https://arxiv.org/pdf/2407.09342

**OpenUAV: A UAV Testbed for the CPS and Robotics Community** — Stony Brook
Not security-specific, but it's the containerized PX4 + Gazebo substrate a lot of this work sits on. Read it for the infrastructure pattern (reproducibility, containerization, multi-user).
https://cybercardia.cs.stonybrook.edu/sites/cybercardia.cs.stonybrook.edu/files/OpenUAV%20A%20UAV%20Testbed%20for%20the%20CPS%20and%20Robotics%20Community.pdf

## Multi-Robot / Fleet Security

**Investigating Security Threats in Multi-Tenant ROS 2 Systems** — Xia et al., ICRA 2025
The single closest fit. Multiple tenants sharing one ROS 2 graph, which is exactly the "lateral movement / trust-propagation across a shared graph" bullet.
https://www.weisongshi.org/papers/xia25-ICRA.pdf

**Automated Discovery of Semantic Attacks in Multi-Robot Navigation Systems** — Yeke et al., USENIX Security 2025 (Purdue PurSec)
Falsified peer state cascading through a fleet, discovered automatically. Artifacts released on Figshare. This is the "swarm coordination-level attacks" bullet done properly, and it also bridges into the Nav2 sensor-spoofing section.
https://www.usenix.org/conference/usenixsecurity25/presentation/yeke · [PDF](https://www.usenix.org/system/files/usenixsecurity25-yeke.pdf)

**Partition-Tolerant and Byzantine-Tolerant Decision-Making for Distributed Robotic Systems with IOTA and ROS 2** — arXiv:2208.13467
Rare in that it's Byzantine-tolerance actually implemented on ROS 2, not in the abstract.
https://arxiv.org/pdf/2208.13467

**Blockchain Technology Secures Robot Swarms: Consensus Protocols and Resilience to Byzantine Robots** — Strobel et al.
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7806104/

**Securing Unmanned Devices in Critical Infrastructure: A Survey of Hardware, Network, and Swarm Intelligence** — Kose, Kose, Liang (Sam Houston State), Electronics 2026, 15(6), 1204
Broad thematic survey rather than a targeted contribution, but the swarm-intelligence pillar of its taxonomy is the framing our fleet-security bullets need, and its "Resource–Security Paradox" (crypto/AI defenses cost flight endurance, and adversaries exploit that via battery-exhaustion attacks) is a clean bridge into the resource-exhaustion topic. Also touches the sim-to-real gap in AI perception and digital forensic readiness — useful as a citation map across several of our sections.
https://www.mdpi.com/2079-9292/15/6/1204 · https://doi.org/10.3390/electronics15061204

## Intrusion / Anomaly Detection for ROS 2 UAV Traffic

**QUADFormer: Learning-Based Detection of Cyber Attacks in Quadrotor UAVs** — Wang, Yang, Yang, Wang, Li, Zhang, IEEE Transactions on Control Systems Technology 34(1), Jan 2026
Transformer-based attack detection built on a residue generator, aimed squarely at the case our detection bullets care about: large outdoor maneuvering flights where the dynamics are nonlinear and the noise is non-Gaussian, which is exactly where statistics-based detectors fall over. Validated in both simulation and real flights, and it includes an alert module for safe task execution under attack, so it reaches into the resilient-control section too. Caveat: features are dynamics-side, not ROS 2 semantics — the cross-domain half of our bullet is still open.
https://ieeexplore.ieee.org/abstract/document/11134535 · https://doi.org/10.1109/TCST.2025.3598255
