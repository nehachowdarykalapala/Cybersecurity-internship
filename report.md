This report is about a local network scan I performed using Nmap inside Kali Linux, running on a UTM virtual machine on my **Windows** system.

---

### 🛠️ Step 1: Check Nmap Installation

I first checked that Nmap was installed by running:

```bash
nmap --version
```

---

### 🌐 Step 2: Find Local IP and Subnet

To find my local IP address and subnet, I used:

```bash
ip a
```

My IP was `192.168.182.128`, and the subnet was `192.168.182.0/24`.

---

### 🚀 Step 3: Run the Network Scan

To scan the whole subnet, I ran:

```bash
sudo nmap -sS 192.168.182.0/24 -oN scan.txt -oX scan.xml
```

This command performed a TCP SYN scan and saved the results in both plain text and XML formats.

---

### 📊 Step 4: Sample Scan Results

The scan gave me a list of devices connected to my network and the ports that were open. For example:

- `192.168.182.128` had **port 80 open** (a web server)
- `192.168.182.133` had **port 22 (SSH)** and **port 445 (SMB)** open

These ports indicate that services like SSH and SMB are running. If not properly configured or secured, these services can pose serious security risks.

---

### 📡 Step 5: Verify Scan Using Wireshark (Optional)

I also opened **Wireshark**, started capturing traffic on the `eth0` interface, and ran the same Nmap scan again.

In Wireshark, I could see:

- **SYN** packets sent from my machine
- **SYN-ACK** or **RST** packets received in response

This confirmed that Nmap was successfully probing for open TCP ports.

---

### 📁 Files I Have Saved

- `scan.txt`: Human-readable Nmap scan output
- `scan.xml`: XML version of the same scan
- `scan.html`: Converted from XML using `xsltproc`
- `capture.pcapng`: Wireshark packet capture
- `screenshots/`: A few screenshots of the terminal and Wireshark

---

### ✅ Conclusion

Doing this task gave me a better understanding of how **Nmap works** and how to use it to scan local networks. I learned:

- What kind of services are usually running on different devices
- How open ports can lead to potential security issues
- That services like **SSH** and **SMB** can be dangerous if exposed without proper security
- How to analyze both scan results and network traffic to confirm behavior

---

## 💻 Environment Details

- **Operating System**: Kali Linux (running in UTM VM on **Windows**)
- **Nmap Version**: 7.95
- **Virtualization Platform**: UTM
- **Local IP**: 192.168.182.128
- **Target Subnet**: 192.168.182.0/24
