# OSPF-Lab

This project is a Cisco Packet Tracer lab that demonstrates the configuration of Open Shortest Path First (OSPF) in Area 0 and how this link-state routing protocol determines the best path based on cost. The lab includes hostname setup, interface configuration, loopback creation, OSPF implementation, reference bandwidth tuning, default route advertisement, and verification through traceroutes and pings.

# Network Topology
## Starting topology before any configurations:

<img width="1740" height="900" alt="image" src="https://github.com/user-attachments/assets/607022ac-4f02-4525-8203-84777b6eb057" />

In this setup, each router is connected to its respective networks, with IP addresses labeled in pink for network subnets, blue for the last digit in the IPv4 address, and yellow for internal IPv4 addresses within each network.

## Step 1 – Hostname & Interface Configuration

### ISPR Configuration at Start
<img width="1434" height="450" alt="image" src="https://github.com/user-attachments/assets/a51cc3b1-9357-4a1a-8eba-a53bb5236245" />

### R1 Configuration at Start
<img width="1593" height="969" alt="image" src="https://github.com/user-attachments/assets/041072ec-8bcf-4162-a708-6e9ec3deb856" />

### R2 Configuration at Start
<img width="1593" height="696" alt="image" src="https://github.com/user-attachments/assets/52cfd53d-7a1e-490f-a89c-f44e52a86117" />

### R3 Configuration at Start
<img width="1575" height="999" alt="image" src="https://github.com/user-attachments/assets/4b7baafd-8eb9-4fff-a3f8-8dd55cba91ed" />

### R4 Configuration at Start
<img width="1521" height="996" alt="image" src="https://github.com/user-attachments/assets/94653bd3-5a2c-4d5d-97c7-9bd629a5be48" />

## Step 2 – Loopback Interfaces

Created a loopback interface on each router to serve as its unique local IPv4 address. These were configured with a /32 subnet mask.

### Loopback IP Assignments:
R1: 1.1.1.1/32
R2: 2.2.2.2/32
R3: 3.3.3.3/32
R4: 4.4.4.4/32

### Example: R1 Loopback Configuration
<img width="1497" height="597" alt="image" src="https://github.com/user-attachments/assets/9d94a0cd-eef2-487a-a3c6-a217b4967c6b" />

## Step 3 – OSPF Configuration

Enabled OSPF on all interfaces and set interfaces not connected to other routers as passive to prevent sending hello packets unnecessarily.

### R1 OSPF Config
<img width="1125" height="339" alt="image" src="https://github.com/user-attachments/assets/f638fe7f-fe41-4003-b982-11936b0adc2e" />

### R2 OSPF Config
<img width="1665" height="465" alt="image" src="https://github.com/user-attachments/assets/28baf00f-54b9-411c-b063-44cd763e764f" />

### R3 OSPF Config
<img width="1623" height="609" alt="image" src="https://github.com/user-attachments/assets/a8a21893-bf99-4ea1-bfd7-9771ac69f66f" />

### R4 OSPF Config
<img width="1611" height="615" alt="image" src="https://github.com/user-attachments/assets/10fae4c9-49f9-4fb2-bdde-60cff8238755" />

## Step 4 – Reference Bandwidth Tuning
Adjusted the reference bandwidth to 10,000 on all routers to influence OSPF cost calculations:
* Fast Ethernet (100 Mbps) cost: 100
* Gigabit Ethernet (1 Gbps) cost: 10

<img width="1380" height="204" alt="image" src="https://github.com/user-attachments/assets/4669ec50-1fee-4307-83d8-d6f0dea54d61" />

## Step 5 – Default Route Advertisement
Configured a static default route on R1 to allow traffic to leave the OSPF area and reach external networks.
Used the default-information originate command to advertise the route to all routers in the OSPF domain.

<img width="879" height="267" alt="image" src="https://github.com/user-attachments/assets/f5428b5c-e889-4a19-815a-50845221521a" />

### Routing Table on R1
<img width="1317" height="753" alt="image" src="https://github.com/user-attachments/assets/690d1fa3-b457-4673-8408-7235f1cb7de4" />

### Routing Table on R4

<img width="1283" height="713" alt="image" src="https://github.com/user-attachments/assets/f0bb871a-ff14-40f4-9db9-26c4daa71ccb" />

In the routing table for R4, you can see the route was advertised. A similar routing table was shown on R2 and R3 as well.

## Step 6 – Path Verification (Traceroute)

### Traceroute 1

<img width="1005" height="411" alt="image" src="https://github.com/user-attachments/assets/d098432f-f9bf-4e7d-8f32-5c671a9c4356" />

From PC1 to R1 Loopback (1.1.1.1): Preferred path was R4 → R2 → R1 due to lower OSPF cost on the gigabit connection.

### Traceroute 2

From PC2 to R2 Loopback (2.2.2.2) showed similar cost-based path preference.

<img width="966" height="390" alt="image" src="https://github.com/user-attachments/assets/2ff46350-9d39-469f-872a-b08c78889193" />

## Final Topology

<img width="1407" height="735" alt="image" src="https://github.com/user-attachments/assets/a8077580-fdf7-4a2f-a8e0-4783f1cfd2a6" />

# Summary & Takeaways
Through this lab, I gained hands-on experience in:
* Configuring hostnames, interfaces, and loopback addresses on multiple routers.
* Implementing and tuning OSPF for optimal path selection.
* Using passive interfaces to reduce unnecessary hello packet traffic.
* Adjusting reference bandwidth to reflect high-speed link advantages.
* Advertising a default route across the OSPF domain.
* Verifying routing behavior with the traceroute command.

Packet Tracer file available in repository.
