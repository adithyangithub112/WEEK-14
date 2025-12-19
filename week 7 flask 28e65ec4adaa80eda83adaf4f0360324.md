# week 7 flask

Status: Done

![Screenshot 2025-11-26 092616.png](Screenshot_2025-11-26_092616.png)

![Screenshot 2025-11-26 092738.png](Screenshot_2025-11-26_092738.png)

### Queries:

In networking, a **query** is **a request for information sent from a client to a server to retrieve specific data**. The most common example is a [Domain Name System (DNS) query](https://www.google.com/search?q=Domain+Name+System+%28DNS%29+query&oq=what+is+queries+in+net&gs_lcrp=EgZjaHJvbWUqCAgBEAAYFhgeMgYIABBFGDkyCAgBEAAYFhgeMggIAhAAGBYYHjINCAMQABiGAxiABBiKBTINCAQQABiGAxiABBiKBTINCAUQABiGAxiABBiKBTIHCAYQABjvBTIHCAcQABjvBTIKCAgQABiABBiiBDIKCAkQABiABBiiBNIBCTE0ODUwajBqN6gCALACAA&sourceid=chrome&ie=UTF-8&mstk=AUtExfC-qT-AyMD7B1_ty98LgBbdq-J0iei9FWBGl7gmAYALvH-iOtKRK65mGmN0V6HTuYPXsNAz0HnN6_PmQdQ7eJPVvSmWvRNwYEinw5s6m7qbyCdSlWeO67u0_e2WHNCVZFrWYrwMPDCn_Izr9OGnwSRzvKCZq6f7kQgHS9UQCNAtFcWsaemYQaXgy2Utyg7k0IwOSsRodK4K4AC1rIHnO6L83ZQA7ab8GNg-fWE2aRLE8O_9YMyMsFv7B1JI0T-o41QTbUNBt1ekE07TGSDO66Kv&csui=3&ved=2ahUKEwjXuI_F9o6RAxX2RmwGHYmqIZoQgK4QegQIARAC), where a computer asks a DNS server for the IP address associated with a domain name. These queries are essential for devices to communicate and function correctly on a network, as they resolve human-readable names into machine-readable IP addresses. 

***Working of LLMNR and NBT-NS***

1. LLMNR (Link Layer Multicast Network Resolution) and NBT-NS (NetBios-Name Service) are two protocols initiated in a LAN if the configured DNS server is unavailable or isn’t able to resolve a network resource name to its actual address. These are also initiated if a machine tries to query for a shared resource which isn’t available in the dns records or there is typo while accessing a shared resource or any host on the network.

![image.png](image.png)

2. Both of these protocols are broadcasted (NBT-NS) or multicasted (LLMNR) in the domain and if the shared resource is avaialable with the name that is queried the machine hosting the shared resource will reply with a response and the client requesting it shares it hashed password and username to authenticate itself so that the server hosting it can check the necessary permissions and determine if the user can access it or not.

![image.png](image%201.png)

1.

![Screenshot 2025-11-26 092738.png](Screenshot_2025-11-26_092738%201.png)

filter :  **llmnr and ip.src == 192.168.232.162**

From packet 52  a LLMNR Query with name - fileshaare , which has been mistyped.

![Screenshot 2025-11-26 094100.png](Screenshot_2025-11-26_094100.png)

1. 

![image.png](image%202.png)

filter : **llmnr and ip.addr == 192.168.232.162**

![Screenshot 2025-11-26 094722.png](Screenshot_2025-11-26_094722.png)

1. 

![Screenshot 2025-11-26 094832.png](Screenshot_2025-11-26_094832.png)

filter:  **ip.addr == 192.168.232.2**15

![Screenshot 2025-11-26 095045.png](Screenshot_2025-11-26_095045.png)

1. 

![Screenshot 2025-11-26 095347.png](Screenshot_2025-11-26_095347.png)

filter:  **ntlmssp.auth.username**

![Screenshot 2025-11-26 095707.png](Screenshot_2025-11-26_095707.png)

1. 

![Screenshot 2025-11-26 095840.png](Screenshot_2025-11-26_095840.png)

filter :   **ntlmssp.auth.username**

![Screenshot 2025-11-26 095829.png](Screenshot_2025-11-26_095829.png)

### ***Mitigations:***

1. Disabling LLMNR and NBT-NS (if it doesn’t disrupt the environment) will help reduce the attack surface and falling victim to such attacks.
2. Ensuring strong password policies.