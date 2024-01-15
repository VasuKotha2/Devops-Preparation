Why is Ngnix called a reverse proxy?

Two common types of proxy are 
* Forward proxy and Reverse Proxy

Forward Proxy:
--------------
* A forward proxy is a server that sits between the group of client machines and the internet. when those clients make requests to websites on the internet, the forward proxy acts as a middleman intercepts those requests and talks to webservers on behalf of those client machines.

Why would anyone wants to do that?

Here are a few reasons.
1. One, a forward proxy protects the client's online identity. By using a forward proxy to connect to a website, the IP address  of the client is hidden from the server. Only the IP address of the proxy is visible. It would be harder to trace back to the client. 
2. Two, a forward proxy can be used to bypass browsing restrictions. Some institutions like governments, schools and big businesses use firewalls to restrict access to the internet. By connecting to a forward proxy outside the firewalls, the client machine can potentially get around these restrictions.
3. A forward proxy can be used to block access to certain content. For example in schools and college networks they will restrict access to social media websites.

A forward proxy normally need clients to configure its application to point to it. For large institutions they usually apply a technique called transparent proxy to streamline the process.

Transparent Proxy:
-----------------
* A transparent proxy works with layer 4 switches to redirect certain types of traffic to the proxy automatically. There is no need to configure the client machines to use it. It is difficult to bypass a transparent proxy when the client is on the institutions network.

Reverse Proxy:
--------------
* A reverse proxy sits between the internet and the web servers. It intercepts the requests from the clients and talks to the web server on behalf of the clients. 

Why would a website uses a reverse proxy?

Here are the few good reasons.
1. One, a reverse proxy could be used to protect a website. The website's IP addresses are hidden behind the reverse proxy and are not revealed to the clients. This makes it much harder to target a DDoS attack against a website.
2. Second, a reverse proxy is used for load balancing. A popular website handling millions of users everyday is unlikely to be able to handle the traffic with a single server. A reverse proxy can balance a large number of incoming requests by distributing the traffic to a large pool of web servers, and effectively preventing any single one of them becoming overloaded
3. Third, a reverse proxy caches static content. A piece of content could be cached on the reverse proxy for a perid of time. If the same piece of content is requested again from the reverse proxy, the locally cached version could be returned quickly. 
4. A reverse proxy can handle SSL encryption. SSL handshake is computationally expensive. A reverse proxy can free up the origin servers from those expensive operations. Instead of handling SSL for all clients, a website only need to handle SSL handshake from a small number of reverse proxies.

https://youtu.be/3N0tGKwvBdA?si=uL7XLiS5ste8gLCf