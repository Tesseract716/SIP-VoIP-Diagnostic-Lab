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

Linux (Ubuntu): Managed via VMware/VirtualBox.

SIP Clients: MicroSIP (Windows) and Linphone (Linux).

Key Troubleshooting Achievements
Fixed Permission Denied: Resolved Wireshark capture errors by reconfiguring wireshark-common and managing user groups.

Protocol Standardization: Corrected "Method Not Allowed" errors by switching transport from TCP to UDP on port 5060.

Call Flow Analysis
Verified the INVITE -> 180 Ringing -> 200 OK handshake.

Successfully captured and analyzed DTMF tones within the RTP stream.
