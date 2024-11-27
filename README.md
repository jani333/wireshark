Wireshark for Beginners: Packet Capture and Filtering

This project documents the steps I followed to install and use Wireshark on Kali Linux as part of the "Wireshark for Beginners: Capture Packets" guided project on Coursera. The goal was to learn how to capture packets, use filters, and extract useful information like the IP address of a loaded website.

Installation on Kali Linux

Wireshark can be installed easily on Kali Linux using the terminal.

Steps to Install Wireshark
Open the terminal in Kali Linux.
Update the package lists:
sudo apt update
Install Wireshark:
sudo apt install wireshark
During installation, you may be asked whether non-superusers should be able to capture packets. Select Yes or configure it later.
Add the current user to the Wireshark group for packet capture:
sudo usermod -aG wireshark $USER
Restart your system or log out and log in for the changes to take effect.
Verify the installation:
wireshark --version
Using Wireshark for Packet Capture

Wireshark is a powerful network protocol analyzer. Below are the steps I followed to capture and filter packets:

1. Opening Wireshark
Launch Wireshark from the terminal by typing:
wireshark
Alternatively, use the application menu to open it.
2. Capturing Packets
Select the network interface to capture packets (e.g., eth0 for Ethernet).
Click on the blue shark fin icon to start capturing packets.
Open a browser and load a website like Google or YouTube while capturing packets.
3. Filtering Packets
To analyze specific traffic:

Use the Filter bar in Wireshark.
Apply the following filter to display only TLS handshake packets:
tls.handshake.type == 1
This filter shows TLS Client Hello packets, which can be used to identify the destination IP address of the website you loaded.
4. Extracting the Destination IP
Locate the Destination field in the filtered packets to find the IP address of the server.
Example from the screenshots:
For YouTube: 142.251.33.174
Entering this IP address in the browser or an online IP-to-URL resolver will open the corresponding website.
Screenshots

Below are screenshots demonstrating the steps:

Installation:
Installing Wireshark on Kali Linux.
Adding User to Wireshark Group:
Granting necessary permissions for packet capture.
Packet Capture Interface:
Launching Wireshark and selecting the network interface.
Filtered Packets:
Using the tls.handshake.type == 1 filter to isolate TLS handshake packets.
Screenshots attached in this repository illustrate each step.

Output Example

Using the steps above:

A filtered packet reveals a Client Hello message with the destination IP address.
For example:
Destination: 142.251.33.174
Entering this IP in the browser redirects to YouTube.
This documentation serves as a reference for network analysis and as an example project on my GitHub portfolio. It showcases my ability to use Wireshark for packet capture and analysis, which is a valuable skill in cybersecurity and networking.
