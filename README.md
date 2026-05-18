# Lab 01: Rolling Buffer Packet Capture

## Objective
I configured Wireshark via to capture smaller packet files (pcaps) so that when a problem occurs, I can simply go back to the capture that was running at the time of the issue.

Specifically, I set Wireshark to:

- ***File size limit***: Each capture file is capped at 500 MB.
- ***Ring buffer***: Wireshark maintains a ring buffer of 10 files.
- ***Overwrite behavior***: Once the 10th file is filled, Wireshark automatically overwrites the first file, then the second, and so on.

This setup ensures continuous packet capture without consuming unlimited disk space. At any given time, I have a rolling history of 10 files × 500 MB each = 5 GB of recent traffic data. This rolling buffer allows me to quickly analyze the packets captured during the exact window when a network problem occurred.


---

## Configuration Steps

### 1. Open Wireshark Capture Options
- Go to **Capture → Options**.
- Select your interface (e.g., `Ethernet`, `Wi-Fi`).

### 2. Set File Size Limit
- In the **Output** tab, choose a base filename (e.g., `capture.pcap`).
- Enable **Create a new file automatically**.
- Enable **after** then set → `500 MB`.
  
### 3. Configure Ring Buffer
- Enable **Ring buffer with 10 files**.
- This means Wireshark will keep 10 files in rotation:
  - File 1 → File 2 → … → File 10 → back to File 1 (overwrite).
    
### 4. Start Capture
- Click **Start**.
- Wireshark will now continuously capture packets, rotating through 10 files


---
<img width="1244" height="716" alt="Rolling-Packet-Capture" src="https://github.com/user-attachments/assets/a2e9a326-fd0e-40e9-82ff-696b89f18d71" />
