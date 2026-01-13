# SIP-VoIP-Diagnostic-Lab
A cross-platform lab analyzing SIP signaling and RTP media flows using Wireshark, MicroSIP, and Linphone.

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
