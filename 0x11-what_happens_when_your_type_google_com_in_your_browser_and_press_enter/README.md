# What happens when you type https://www.google.com in your browser and press Enter

Reviewing and encapsulating networking knowledge and skills I had been learning
and practicing over the last month, in this project, I wrote a blog post
answering the classic interview question - what happens when you enter [generic
website] into a browser and hit `Enter`?

## Tasks :page_with_curl:

### What Happens When You Type https://www.google.com and Press Enter

When you type "https://www.google.com" into your browser and press Enter, a complex series of events occurs in the background, allowing you to seamlessly access Google's homepage. Here's a detailed look at the process:

#### 1. DNS Request
The journey begins with a DNS (Domain Name System) request. Your browser doesn't understand "www.google.com" directly; it needs the corresponding IP address. 

1. **Browser Cache**: The browser first checks its cache to see if it already has the IP address for Google.
2. **Operating System Cache**: If not found, it queries the OS cache.
3. **Router Cache**: The next stop is the router's cache.
4. **ISP DNS Server**: If the IP address is still not found, the request is sent to your ISP's DNS server.
5. **Recursive Search**: If the ISP's DNS server doesn't have it, it performs a recursive search, querying root DNS servers, then TLD (Top-Level Domain) servers, and finally authoritative servers for "google.com".

The DNS server responds with the IP address of Google's servers.

#### 2. TCP/IP
With the IP address in hand, your browser initiates a TCP (Transmission Control Protocol) connection using the IP (Internet Protocol).

1. **Three-Way Handshake**: The browser and Google's server perform a three-way handshake to establish a reliable connection.
   - **SYN**: The browser sends a SYN (synchronize) packet to the server.
   - **SYN-ACK**: The server responds with a SYN-ACK (synchronize-acknowledge) packet.
   - **ACK**: The browser sends an ACK (acknowledge) packet back to the server.

This handshake establishes a reliable communication channel between your browser and the server.

#### 3. Firewall
As the packets travel through the internet, they pass through multiple firewalls.

1. **Local Firewall**: Your computer’s firewall ensures outgoing traffic is legitimate.
2. **Network Firewall**: Your router or ISP might have its own firewall that checks and filters packets.
3. **Server-Side Firewall**: Google's servers are protected by sophisticated firewalls that filter out malicious traffic and allow legitimate requests.

#### 4. HTTPS/SSL
Google uses HTTPS (Hypertext Transfer Protocol Secure) to encrypt the data exchanged between your browser and its servers. This is facilitated by SSL/TLS (Secure Sockets Layer/Transport Layer Security).

1. **SSL Handshake**: Your browser and Google's server perform an SSL handshake to establish a secure connection.
   - **Certificate Exchange**: The server sends its SSL certificate to the browser.
   - **Certificate Verification**: The browser verifies the certificate’s validity.
   - **Session Keys**: Both parties agree on session keys for encryption.

Once the handshake is complete, all data transmitted is encrypted, ensuring privacy and security.

#### 5. Load-Balancer
To manage the massive traffic, Google employs load balancers.

1. **Request Distribution**: The load balancer distributes incoming requests across multiple servers.
2. **Health Checks**: It constantly monitors the health of servers and ensures traffic is only directed to healthy servers.
3. **Scalability**: Load balancers help Google scale its services efficiently, handling millions of requests per second.

#### 6. Web Server
The load balancer directs your request to one of Google's web servers.

1. **Request Handling**: The web server receives your request for "https://www.google.com".
2. **Static Content**: If the request is for static content (like images, CSS, or JavaScript files), the web server serves these directly.

#### 7. Application Server
For dynamic content, the web server forwards the request to an application server.

1. **Processing Logic**: The application server processes the request, executing backend logic, and generating a dynamic response.
2. **Inter-Service Communication**: It may interact with other services and APIs to gather necessary data.

#### 8. Database
Often, the application server needs to query a database to fetch or store data.

1. **Database Query**: The application server sends a query to the database.
2. **Data Retrieval**: The database retrieves the requested data and sends it back to the application server.
3. **Response Construction**: The application server uses this data to construct the final response.

#### Final Steps: Response Delivery and Rendering
1. **Response Transmission**: The application server sends the response back to the web server.
2. **Encryption**: The response is encrypted via SSL/TLS and sent back to your browser.
3. **Rendering**: Your browser decrypts the response and renders the HTML, CSS, and JavaScript, displaying Google's homepage.

In summary, this intricate process involves DNS resolution, secure TCP/IP communication, firewall security, load balancing, web and application server coordination, and database interactions—all working in unison to deliver a seamless browsing experience.

