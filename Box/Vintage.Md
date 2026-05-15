## Vintage 

#### 1)What tool did the attacker use to fuzz the web server ? (Format- include version e.g, nmap@7.80)

### a)Start my search 
http && tcp.ack == 0

#### b)http.user_agent and i find User-Agent: Fuzz Faster U Fool v2.1.0-dev

#### 2)Which subdomain did the attacker discover?

### a)Search this question dns , tls ...

### b)search ip.src_host && http && tcp.srport

and find cloud

### 3)How many login attempts did the attacker make before successfully logging in to the dashboard?

## a)I'm search not ok with access cloud 
Ce qui ma permet de determiner le sousdomaine qui a ete hack
Ftcp.ack == 1 && tcp.srcport && http 

[Full request URI: http://cloud.vantage.tech/dashboard/auth/login/]
http.user_agent == "Fuzz Faster U Fool v2.1.0-dev"

Avant le paquet 26081

http.request.version == "HTTP/1.1"  && http.user_agent == "Fuzz Faster U Fool v2.1.0-dev"

Fuzz Faster sert juste a determiner si c'est un sous domaine !

