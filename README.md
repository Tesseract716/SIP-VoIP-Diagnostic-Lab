# SIP-VoIP-Diagnostic-Lab
A cross-platform lab analyzing SIP signaling and RTP media flows using Wireshark, MicroSIP, and Linphone.

## 🛡️ System Administration & Networking
To ensure a stable testing environment, I implemented standard administrative best practices:

1. **Snapshots:** Created a VMware Snapshot prior to system-level changes to ensure a 0-second Recovery Time Objective (RTO) in case of configuration failure.
2. **Network Mapping:** - **Linux IP:** Identified via `ip a` on the `ens33` interface.
   - **Windows IP:** Identified via `ipconfig` on the host machine.
   - **Verification:** Performed an ICMP 'ping' test between the host and guest to validate the network path before launching SIP applications.

Project: SIP/RTP Packet Analysis Lab
Objective
To analyze the SIP handshake and RTP media stream between a Windows host and a Linux VM.

Technologies Used
Wireshark: For packet-level diagnostics.

Linux (Ubuntu): Managed via VMware.
SIP Clients: MicroSIP (Windows) and Linphone (Linux).

Key Troubleshooting Achievements
Fixed Permission Denied: Resolved Wireshark capture errors by reconfiguring wireshark-common and managing user groups.

Protocol Standardization: Corrected "Method Not Allowed" errors by switching transport from TCP to UDP on port 5060.

Call Flow Analysis
Verified the INVITE -> 180 Ringing -> 200 OK handshake.

Successfully captured and analyzed DTMF tones within the RTP stream.

### Section 1: Manual Endpoint Provisioning
"I manually provisioned two disparate SIP endpoints—MicroSIP on Windows and Linphone on Ubuntu—to establish a Peer-to-Peer (P2P) environment. By configuring the SIP Domain and Proxy to point directly to the local IPv4 addresses, I bypassed the need for a registrar and standardized the communication on UDP Port 5060."

[MicroSIP Step 1]
[MicroSIP Step 2]
[MicroSIP Final Config]
[Linphone Step 1]
[Linphone Final Config]

---

### Section 2: Encountering and Resolving System Constraints
"During the diagnostic phase, I encountered a Linux security constraint where Wireshark lacked the necessary permissions to capture on the ens33 interface. I resolved this by reconfiguring the wireshark-common package and using usermod to grant the user profile capture privileges, following the principle of least privilege."

![Wireshark Permission Error]
![Linux Terminal Fix]

---

### Section 3: Execution and Signaling Verification
"I successfully executed a cross-platform call. The screenshots show the outbound request from MicroSIP and the corresponding arrival of the SIP INVITE on the Linux guest. This verified that the network bridge and OS firewalls were correctly configured to allow real-time signaling."

[MicroSIP Dialing]
[Signaling Arrival on Linux]
[Active Call Session]

---

### Section 4: Deep-Dive Packet Analysis
"Using Wireshark’s VoIP Call Flow tool, I performed a post-call analysis to validate the session integrity. The capture verifies the standard 3-way handshake (INVITE -> 180 Ringing -> 200 OK) and the transition to RTP (g711A) for media transmission. I also successfully captured DTMF events, proving the system's ability to handle user touch-tone inputs."

[Wireshark Call Flow Ladder Diagram]
