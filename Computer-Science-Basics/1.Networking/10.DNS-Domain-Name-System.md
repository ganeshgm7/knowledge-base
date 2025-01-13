# DNS (Domain Name System)

DNS, or Domain Name System, is like the internet's phonebook. When you type a website's name (e.g., `netflix.com`) into your browser, DNS translates that name into an IP address (e.g., `44.240.158.19`) that computers use to locate each other on the internet.

## Why DNS is Necessary
Humans find it easier to remember domain names rather than numerical IP addresses. However, computers need IP addresses to communicate. DNS bridges this gap by translating domain names into IP addresses, making the internet more user-friendly.

## How DNS Works

### When You Try to Visit a Website:

1. **User Requests a Domain**:  
   You type `netflix.com` into your browser.

2. **DNS Query**:  
   Your device sends a query to a DNS resolver to find the IP address for `netflix.com`.

3. **DNS Resolver Checks Cache**:  
   The DNS resolver first checks its cache to see if it has recently requested the IP address for `netflix.com`.

4. **Walking the DNS Tree**:  
   If the resolver doesn’t have the IP address cached, it begins a process called "walking the DNS tree," querying a series of DNS servers:
   
   - **Root DNS Server**: Knows the top-level domains (TLDs, such as `.com`, `.org`, etc.) and directs the query to the `.com` server.
   - **TLD DNS Server**: The `.com` server knows which DNS servers have the IP address for `netflix.com` and sends the query to one of those.
   - **Authoritative DNS Server**: This server knows the exact IP address for `netflix.com` and returns it to the DNS resolver.

5. **Return IP to User**:  
   The DNS resolver sends the IP address back to your computer, allowing your browser to connect to `netflix.com` and load the website.

## Entities Involved in DNS

- **DNS Resolver**:  
  This is the DNS server that your computer queries first. It acts as an intermediary, querying other DNS servers for the IP address of the domain you want to visit.

- **Root DNS Servers**:  
  These are the highest level of DNS servers. There are only 13 root servers globally, and they know where to find the TLD servers.

- **Top-Level Domain (TLD) DNS Servers**:  
  These servers manage domains under specific TLDs like `.com`, `.org`, or `.net`.

- **Authoritative DNS Servers**:  
  These are the final servers in the DNS lookup chain. They know the IP address associated with a specific domain.

## Why Not Use Just One DNS Server?

Using just one DNS server is impractical because:

- **Scalability**:  
  There are millions of domains and billions of users. A single DNS server couldn't handle the massive volume of requests.

- **Redundancy**:  
  Multiple DNS servers ensure that if one server fails, others can take over, maintaining the stability and reliability of the DNS system.

## DNS Key Terms

- **DNS Zone**:  
  A portion of the DNS namespace managed by a specific DNS server.

- **Zone File**:  
  The file on a DNS server containing the mappings between domain names and IP addresses.

- **Name Server (NS)**:  
  The server hosting one or more DNS zones and providing the IP addresses for the domain names within those zones.

- **Authoritative**:  
  A DNS server that provides the definitive answer for a domain’s IP address.

- **Non-Authoritative (Cached)**:  
  DNS responses that are stored temporarily to speed up subsequent queries.

## Registering a Domain

When you register a domain:

1. **Purchase a Domain**:  
   You buy `cats.com` from a domain registrar.

2. **Create a DNS Zone**:  
   The registrar creates a DNS zone for `cats.com` and sets up the necessary records (like A records for IP addresses).

3. **Set Up Name Servers**:  
   The domain registrar sets up name servers (NS records) that point to the DNS servers hosting your domain's zone files.

4. **Domain Goes Live**:  
   Once the DNS information is propagated, your domain `cats.com` is live and can be resolved by DNS queries globally.

## Example: Browsing a Domain

When you type `www.netflix.com` into your browser:

1. **Query Start**:  
   Your device checks its local cache for the IP of `www.netflix.com`. If it’s not there, the device sends a DNS query to the DNS resolver.

2. **DNS Resolver Process**:  
   - The DNS resolver checks its cache. If no record is found, it asks the root DNS server.
   - The root DNS server responds with the address of the TLD server responsible for `.com`.
   - The DNS resolver queries the TLD server, which returns the address of the authoritative server for `netflix.com`.
   - The DNS resolver queries this authoritative server, which returns the IP address of `www.netflix.com`.

3. **Connecting to the Website**:  
   With the IP address in hand, your browser connects to `www.netflix.com`, and the website begins to load.

This entire process usually takes just a few milliseconds, allowing users to access websites almost instantly.
