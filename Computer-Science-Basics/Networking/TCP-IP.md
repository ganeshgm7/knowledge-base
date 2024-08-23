# TCP/IP Model

The TCP/IP model, also known as the Internet Protocol Suite, is a conceptual framework used to describe the functions of a networking system. It is the foundation of the modern internet, enabling communication between computers across various networks. TCP/IP stands for Transmission Control Protocol/Internet Protocol.

## What Does TCP/IP Do?

TCP/IP is responsible for transferring data between devices, ensuring that the data sent by one computer is received accurately by another. To maintain accuracy, TCP/IP breaks the data into smaller packets, which are reassembled at the destination. This process ensures the information arrives correctly. TCP/IP is widely used in the real-world internet, where various physical media and network technologies exist. Instead of being tied to a specific physical setup, the TCP/IP model is flexible, allowing it to work with different physical implementations.


<p align="center">
  <img src="../../Images/TCP-IP.webp" alt="TCP IP">
</p>

## TCP/IP Layers

The TCP/IP model is composed of four layers:

### 1. Network Interface Layer (Link Layer)

- **Function:** Handles the physical and data link layer tasks.
- **Key Protocols:** Ethernet, Wi-Fi, ARP, PPP.
- **Equivalent OSI Layers:** Combines the OSI Model's Physical and Data Link layers.

### 2. Internet Layer

- **Function:** Manages the addressing, routing, and packaging of data.
- **Key Protocols:** IP (IPv4, IPv6), ICMP, ARP.
- **Equivalent OSI Layer:** Corresponds to the OSI Model's Network layer.

### 3. Transport Layer

- **Function:** Provides reliable data transfer services to the upper layers.
- **Key Protocols:** TCP, UDP.
- **Equivalent OSI Layer:** Corresponds to the OSI Model's Transport layer.

### 4. Application Layer

- **Function:** Provides protocols for specific data communication services on a process-to-process level.
- **Key Protocols:** HTTP, FTP, SMTP, DNS, SSH.
- **Equivalent OSI Layers:** Combines the OSI Model's Session, Presentation, and Application layers.

The TCP/IP model, evolving from the OSI model, simplifies and consolidates the OSI layers into four primary layers, making it more practical for real-world network implementations. While the OSI model offers a more detailed theoretical framework, the TCP/IP model's simplicity and widespread use make it the backbone of modern networking. Understanding both models is essential for network design, implementation, and troubleshooting.

## Example: Luffy Sends an E-mail to His Friend Zoro

### 1. Luffy Sends the Email

- **Application Layer (Layer 4):** Luffy uses an email app (like Gmail) to write and send an email to Zoro. The app uses a protocol called SMTP to prepare the email and send it to Luffy’s mail server.
- **Transport Layer (Layer 3):** The email is broken into smaller pieces for easier transmission. A protocol called TCP ensures these pieces are sent reliably and in the correct order to Zoro’s mail server.
- **Internet Layer (Layer 2):** Each piece of the email is packed into packets with the address of Zoro’s mail server. The Internet Protocol (IP) is responsible for getting these packets to the right destination through various networks.
- **Network Access Layer (Layer 1):** The packets are converted into signals (like electrical signals for wired networks or radio waves for wireless networks) and sent through the network to reach Zoro’s mail server.

### 2. Zoro Receives the Email

- **Network Access Layer (Layer 1):** Zoro’s device receives the signals and converts them back into packets.
- **Internet Layer (Layer 2):** The packets are checked and routed correctly to the application on Zoro’s device.
- **Transport Layer (Layer 3):** The pieces of the email are put back together in the right order by TCP, ensuring nothing is missing or out of place.
- **Application Layer (Layer 4):** Zoro’s email app receives the complete email and displays it so he can read it.
