# Docker Network Simulator

This project simulates a simple Docker-based network with DHCP, routing, and multiple containers. It demonstrates network communication between containers across different subnets, using a router to route traffic between them.

## Project Structure

- **dhcp-server**: A container running `dnsmasq` that provides DHCP services within the `subnet1` network, assigning IPs in the range `192.168.1.10` to `192.168.1.100`.
- **client1**: A client container in `subnet1`, configured to sleep indefinitely.
- **client2**: A client container in `subnet2`, also configured to sleep indefinitely.
- **router**: A container running Alpine Linux with `iproute2`, acting as a router between `subnet1` and `subnet2`. It is configured to forward IP packets between the two subnets.

## Features

- **DHCP Server**: Automatically assigns IP addresses to containers in `subnet1`.
- **Routing**: A router container forwards packets between `subnet1` and `subnet2`.
- **Multiple Subnets**: Simulates two isolated subnets, allowing for communication through the router.

## Requirements

- Docker Engine installed.
- Docker Compose (optional for ease of use).

## Usage

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/ShravannJain/DockerNetLabs.git
   cd DockerNetLabs

2. **Build and Start the Containers**:
   ```bash
   docker compose up

3. **Access the Containers**:
   ```bash
   docker exec -it <container_name> sh

4. **Verify Network Setup**

- **client1** in `subnet1` should receive an IP from the DHCP server (in the range `192.168.1.10-100`).
- **client2** in `subnet2` should have an IP assigned manually by DHCP server which has dnsmasq image.
- The **router** should have IPs in both subnets (`192.168.1.x` and `192.168.2.x`).

5. **Testing Connectivity**
- From `client1`, ping `client2` (which ofc are in different subnet btw)
  ```bash
  ping <client2_ip>
- Ensure routing is working properly, and the router is forwarding packets between the two subnets.

   
  




