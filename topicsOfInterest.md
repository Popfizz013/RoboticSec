# Topics of Interest

## ROS 2 Security (beyond the RTPS/DDS transport layer)
- ROS 2 graph/API layer security (services, actions, parameters, lifecycle)
- Control-plane service abuse (`/controller_manager/*`: switch/load/unload/configure controllers)
- Parameter service mutation (relaxing runtime safety limits, PID gains, update rates)
- Lifecycle transition abuse (`ChangeState` as targeted DoS)
- Feedback / world-model poisoning as an attack class (`/joint_states`, `/tf`, `/scan`, `/points`, `/odom`, `/camera_info`)
- Violating manipulator safety invariants using well-formed, in-spec ROS 2 API calls
- Clock / timestamp / freshness manipulation (`/clock`, TF extrapolation, replay windows)
- micro-ROS / DDS-XRCE Agent as a less-audited protocol surface
- rosbridge_suite (JSON-over-WebSocket, often exposed without auth)
- SROS2 enclaves / permissions.xml governance gaps (CVE-2023-50257 class)

## Multi-Robot / Fleet Security
- Cross-domain and multi-robot discovery-layer trust
- ROS_DOMAIN_ID hygiene and discovery-server trust
- Lateral movement / trust-propagation across a shared ROS 2 graph
- Swarm / coordination-level attacks (falsified peer state cascading through a fleet)

## Sensor Spoofing → Autonomy Decisions
- Sensor-spoofing to autonomy-decision bridge (Nav2 especially)
- Minimal perturbations to costmaps/scans that flip planner decisions or defeat recovery behaviors

## Intersection of Drone Security and ROS
- uXRCE-DDS offboard-control bridge as a flight-control attack surface (PX4 / ArduPilot)
- Cross-protocol trust translation (MAVLink ↔ DDS/ROS) and where guarantees are lost
- Estimator / sensor-state poisoning surfaced through ROS (GPS, odometry, VIO, optical flow → EKF)
- Failsafe / offboard state-machine evasion (arming checks, geofence, failsafe suppression)
- Multi-UAV / swarm graph pivoting over a shared DDS domain

## Secure Communication & Key Management for UAV Fleets
- Lightweight, scalable identity and key distribution (hierarchical CAs, per-mission certs, fast re-keying)
- Evaluating SROS2 over lossy, high-latency links (4G/5G, mesh RF): latency, jitter, control stability
- Hybrid security architectures (DDS security + link-layer protections like IPsec/WireGuard)

## Resilient Control & Safe Degradation Under Attack
- Resilient control architectures tolerating MitM, spoofing, or DoS on ROS 2 topics
- Security-aware autonomy (mission planners that adapt to detected threat level)
- Formal links between cyber indicators and safety envelopes

## Intrusion / Anomaly Detection for ROS 2 UAV Traffic
- Feature design combining ROS 2 semantics with UAV dynamics
- Lightweight on-board detection under strict CPU/power budgets
- Cross-domain learning (train in sim, adapt to real drones)

## DDoS / Resource-Exhaustion Attacks on ROS 2 UAV Networks
- Modeling UAV nodes under flood attacks (callback latency, control-loop timing, stability margins)
- Mitigation (per-topic rate limiting, admission control, prioritized scheduling, blackholing)
- Joint cyber-physical performance metrics (time-to-instability, trajectory deviation, mission failure probability)

## Secure Simulation Frameworks & Datasets
- Extending ROS 2 UAV simulators (PX4 + Gazebo/Ignition) with attack injection and full telemetry logging
- Public intrusion-detection datasets for ROS 2 UAVs with labeled attack/normal phases
- Benchmark suites for security–performance trade-offs
