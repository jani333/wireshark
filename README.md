

---

# Wireshark for Beginners: Packet Capture and Filtering

This project documents the steps I followed to install and use Wireshark on Kali Linux as part of the "Wireshark for Beginners: Capture Packets" guided project on Coursera. The goal was to learn how to capture packets, use filters, and extract useful information like the IP address of a loaded website.

## **Installation on Kali Linux**
Wireshark can be installed easily on Kali Linux using the terminal.

### **Steps to Install Wireshark**
1. Open the terminal in Kali Linux.
2. Update the package lists:
   ```bash
   sudo apt update
   ```
3. Install Wireshark:
   ```bash
   sudo apt install wireshark
   ```
   <img width="1470" alt="Screenshot 2024-11-26 at 7 05 07 PM" src="https://github.com/user-attachments/assets/8a7610fc-1972-4ace-9c19-4e9786a1c6b4">

4. During installation, you may be asked whether non-superusers should be able to capture packets. Select **Yes** or configure it later.
5. Add the current user to the Wireshark group for packet capture:
   ```bash
   sudo usermod -aG wireshark $USER
   ```
   <img width="1470" alt="Screenshot 2024-11-26 at 7 05 07 PM" src="https://github.com/user-attachments/assets/93a4d721-6a33-4ab4-9ab2-065c5eb199f0">

6. Restart your system or log out and log in for the changes to take effect.
7. Verify the installation:
   ```bash
   wireshark --version
   ```

## **Using Wireshark for Packet Capture**
Wireshark is a powerful network protocol analyzer. Below are the steps I followed to capture and filter packets:

### **1. Opening Wireshark**
- Launch Wireshark from the terminal by typing:
  ```bash
  wireshark
  ```
  <img width="1470" alt="Screenshot 2024-11-26 at 7 06 47 PM" src="https://github.com/user-attachments/assets/d4224f9f-2283-4aa2-9e29-5301359abae5">

- Alternatively, use the application menu to open it.

### **2. Capturing Packets**
- Select the network interface to capture packets (e.g., `eth0` for Ethernet).
- Click on the **blue shark fin icon** to start capturing packets.
- Open a browser and load a website like Google or YouTube while capturing packets.

### **3. Filtering Packets**
To analyze specific traffic:
- Use the **Filter** bar in Wireshark.
- Apply the following filter to display only TLS handshake packets:
  ```bash
  tls.handshake.type == 1
  ```
  <img width="1470" alt="Screenshot 2024-11-26 at 7 14 56 PM" src="https://github.com/user-attachments/assets/2977c598-b527-45ab-bb90-5d585a6bb327">

  This filter shows TLS Client Hello packets, which can be used to identify the destination IP address of the website you loaded.

### **4. Extracting the Destination IP**
- Locate the `Destination` field in the filtered packets to find the IP address of the server.
- Example from the screenshots:
  - For YouTube: `142.251.33.174`
- Entering this IP address in the browser or an online IP-to-URL resolver will open the corresponding website.

## **Screenshots**
Below are screenshots demonstrating the steps:
1. **Installation**:
   - Installing Wireshark on Kali Linux.
2. **Adding User to Wireshark Group**:
   - Granting necessary permissions for packet capture.
3. **Packet Capture Interface**:
   - Launching Wireshark and selecting the network interface.
4. **Filtered Packets**:
   - Using the `tls.handshake.type == 1` filter to isolate TLS handshake packets.

*Screenshots attached in this repository illustrate each step.*

## **Output Example**
Using the steps above:
- A filtered packet reveals a `Client Hello` message with the destination IP address.
- For example:
  - Destination: `142.251.33.174`
  - Entering this IP in the browser redirects to **YouTube**.

---

This documentation serves as a reference for network analysis and as an example project on my GitHub portfolio. It showcases my ability to use Wireshark for packet capture and analysis, which is a valuable skill in cybersecurity and networking.

---

