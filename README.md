# MCC-Network-Solution

# Choosing the Right Network Topology

Selecting the optimal network topology for a multiplayer game can sometimes be challenging. However, by analyzing the structure and gameplay mechanics of our project, the best option becomes clearer.

## Game Structure Overview

MCC revolves around two main players:
- Operator: the trainee who actively participates in the training session.
- Supervisor: the instructor who observes and monitors the Operator’s performance during the session.

In our setup, both the Operator and the Supervisor are expected to be located in the same physical environment and connected to the same local area network (LAN).

## Recommended Topology: Host-Client (Listen Server)

Given this configuration, the most suitable networking model is the Host-Client topology, also known in Unreal Engine as a Listen Server setup.
In this model:
- The Supervisor’s machine will act as the Server (Host).
- The Operator’s machine will act as the Client.

This means that whenever an Operator wants to start a training session, they will simply connect to the Supervisor’s device, which hosts the server instance locally.

## Network Architecture Diagram

The following diagram illustrates the network architecture used in our setup. The Supervisor acts as the host (server) while the Operator connects as a client over the local network (LAN). This structure ensures direct and efficient communication between both devices without external routing.

<img width="2160" height="1480" alt="Blank diagram (3)" src="https://github.com/user-attachments/assets/37da08cd-8a71-499c-af03-be91be14440d" />

<img width="2160" height="1480" alt="Blank diagram (5)" src="https://github.com/user-attachments/assets/98eae661-50c3-42a0-819f-7ad961ccb98f" />

## Benefits of Using a Host-Client (Listen Server) Model

1. **Performance:** Since all network traffic remains within the local network, the overall performance will be faster and more stable compared to solutions that rely on external servers or the internet.

2. **Security:** Traffic confined within the LAN greatly improves security. No external internet routing means the connection is isolated from external access or interception attempts.

3. **Simplicity and Fewer Networking Issues:** Using a LAN-based connection helps avoid common network complications, such as NAT traversal, port forwarding, or relay server dependencies.

## Networking Architecture and Prediction

Given that the Supervisor and Operator are in the same location and on the same LAN, and that the Supervisor monitors every step taken by the Operator, there is no need to implement Client-Side Prediction for the Operator.

Instead:
- The Operator can directly update their Transform (position, rotation, etc.), and their biometrics.
- These updates are then sent to the Server (Supervisor) for synchronization.

In this controlled LAN-based environment, prediction layers is unnecessary, simplifying the implementation.

## Alternative Setup: Remote Connection via VPN

If the Supervisor and Operator are not connected to the same LAN, we can use a Virtual Private Network (VPN) to simulate a private local connection. Through a VPN tunnel, the Operator will be able to see the Supervisor’s device and connect to it directly as if both were on the same local network.

<img width="2162" height="423" alt="VPN Tunnel" src="https://github.com/user-attachments/assets/00d02a70-9da4-4f57-80f7-85d633a65e71" />
