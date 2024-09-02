# SSL and TLS

**SSL (Secure Sockets Layer)** and **TLS (Transport Layer Security)** are protocols designed to provide secure communication over a computer network. They ensure that data sent between a client (like your web browser) and a server (like a website) is encrypted and secure from eavesdropping or tampering.

## Difference Between SSL and TLS

- **SSL**: The original protocol developed by Netscape in the mid-1990s. It has undergone several versions (SSL 2.0, SSL 3.0) but is now considered outdated due to security vulnerabilities.
- **TLS**: The successor to SSL, first introduced in 1999 as TLS 1.0. It’s an improved version of SSL, with better security features. TLS has evolved with versions such as TLS 1.1, TLS 1.2, and TLS 1.3 (the latest and most secure version).

## How SSL/TLS Works

The process of establishing a secure connection using SSL/TLS involves several steps, commonly referred to as the "SSL/TLS Handshake". Here’s a simplified explanation:

1. **Client Hello**: The client (e.g., your browser) sends a "Client Hello" message to the server (e.g., a website), including the SSL/TLS version it supports, a list of supported cipher suites (encryption algorithms), and other data needed for establishing a secure connection.

2. **Server Hello**: The server responds with a "Server Hello" message, including the SSL/TLS version and cipher suite selected by the server and a digital certificate. The digital certificate contains the server's public key and is used to prove the server's identity.

3. **Authentication**: The client verifies the server’s certificate with a trusted Certificate Authority (CA). If the certificate is valid (not expired or revoked, and the domain name matches), the client proceeds to the next step.

4. **Key Exchange**: The client and server exchange keys. Initially, asymmetric encryption (using public and private keys) is used to securely exchange a shared secret. Once this shared secret is established, both sides switch to symmetric encryption, which is faster and more efficient for ongoing communication.

5. **Secure Communication**: After the handshake is complete and keys are exchanged, the client and server use the agreed-upon encryption method to communicate securely. All data exchanged between them is encrypted.

## Where SSL/TLS is Used

SSL/TLS is widely used in various applications where secure communication is essential. Some common use cases include:

- **Web Browsing**: HTTPS websites use SSL/TLS to encrypt data between the browser and the web server, ensuring that sensitive information (like passwords, credit card numbers, etc.) is secure.
- **Email**: SSL/TLS is used in email protocols like SMTP, POP3, and IMAP to secure emails in transit.
- **VPNs (Virtual Private Networks)**: Many VPNs use SSL/TLS to create secure connections between devices.
- **Instant Messaging**: Some messaging apps use SSL/TLS to secure communications between users.

## Types of SSL/TLS Certificates

There are different types of SSL/TLS certificates based on the level of validation required:

- **Domain Validated (DV) Certificates**: These are the most basic type, where the CA only verifies the ownership of the domain.
- **Organization Validated (OV) Certificates**: The CA verifies the domain ownership as well as some organizational details (like the company name and address).
- **Extended Validation (EV) Certificates**: These provide the highest level of validation, with rigorous checks on the organization. Websites with EV certificates often display a green address bar in the browser.
- **Wildcard Certificates**: These are used to secure multiple subdomains under a single domain (e.g., `*.example.com`).
- **Multi-Domain (SAN) Certificates**: These can secure multiple domains and subdomains under a single certificate.

## Summary

- **SSL/TLS** provides privacy and data integrity between client and server by encrypting the communication.
- The process involves a handshake where both client and server agree on encryption methods, verify identities, and then establish a secure session.
- SSL is the older, less secure version, while TLS is the modern, more secure version.
- SSL/TLS is essential for protecting sensitive data in web browsing, email, and other online activities.

---

# High-Level Guide: Configuring SSL/TLS for a GoDaddy Domain on IIS

### 1. Purchase an SSL/TLS Certificate from GoDaddy
- **Log in to GoDaddy**: Access your account and navigate to the SSL/TLS section.
- **Buy an SSL/TLS Certificate**: Choose the type of certificate (Single Domain, Wildcard, or Multi-Domain) that fits your needs.
- **Set Up the Certificate**: Initiate the setup process for your purchased certificate.

### 2. Generate a CSR (Certificate Signing Request) in IIS
- **Open IIS Manager**: On your server, launch IIS Manager.
- **Create a CSR**: Navigate to the "Server Certificates" section and generate a new CSR by providing your domain and company details.
- **Save the CSR**: The CSR will be saved as a file on your server.

### 3. Submit the CSR to GoDaddy
- **Submit CSR**: Copy the generated CSR and paste it into the required field in your GoDaddy account during the certificate setup process.
- **Domain Validation**: Complete the domain validation process through email, DNS, or file upload as guided by GoDaddy.
- **Download the SSL Certificate**: After validation, download the issued SSL certificate from your GoDaddy account.

### 4. Install the SSL Certificate on IIS
- **Return to IIS Manager**: Go back to the "Server Certificates" section.
- **Complete Certificate Request**: Use the "Complete Certificate Request" option to install the downloaded SSL certificate.
- **Assign Certificate to the Website**: Bind the SSL certificate to your website in IIS by adding an HTTPS binding.

### 5. Configure Your Website to Use HTTPS
- **Force HTTPS**: Optionally, set up URL Rewrite in IIS to redirect all HTTP traffic to HTTPS.
- **Test the Configuration**: Verify that the SSL certificate is working by visiting your site with `https://` and checking for the secure padlock icon.

### 6. Maintain the SSL/TLS Certificate
- **Monitor and Renew**: Ensure the certificate is renewed before it expires. GoDaddy will send reminders, and the renewal process is similar to the initial setup.
