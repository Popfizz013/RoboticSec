# RoboticSec

Liam and Sung-yu are conducting research into the following topic:

**uXRCE-DDS / ROS 2 UAV Security Landscape**

## Starting point

This research builds from [CVE-2026-1579](https://www.cve.org/CVERecord?id=CVE-2026-1579) — a critical (CVSS 9.3) missing-authentication flaw (CWE-306) in the PX4 Autopilot MAVLink interface, where unsigned MAVLink messages can grant interactive shell access. We use this as our direct starting point before pivoting to the uXRCE-DDS / ROS 2 transport.
