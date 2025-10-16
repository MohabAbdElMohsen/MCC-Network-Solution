# MCC-Network-Solution

# Choosing the Right Network Topology for Our Multiplayer Game

Selecting the optimal network topology for a multiplayer game can sometimes be challenging. However, by analyzing the structure and gameplay mechanics of our project, the best option becomes clearer.

## Game Structure Overview

Our game revolves around two main players:
- Operator: the trainee who actively participates in the training session.
- Supervisor: the instructor who observes and monitors the Operator’s performance during the session.

In our setup, both the Operator and the Supervisor are expected to be located in the same physical environment and connected to the same local area network (LAN).

## Recommended Topology: Host-Client (Listen Server)

Given this configuration, the most suitable networking model is the Host-Client topology, also known in Unreal Engine as a Listen Server setup.
In this model:
- The Supervisor’s machine will act as the Server (Host).
- The Operator’s machine will act as the Client.

This means that whenever an Operator wants to start a training session, they will simply connect to the Supervisor’s device, which hosts the server instance locally.

## Benefits of Using a Host-Client (Listen Server) Model

1. Performance
Since all network traffic remains within the local network, the overall performance will be faster and more stable compared to solutions that rely on external servers or the internet.

2. Security
Traffic confined within the LAN greatly improves security. No external internet routing means the connection is isolated from external access or interception attempts.

3. Simplicity and Fewer Networking Issues
Using a LAN-based connection helps avoid common network complications, such as NAT traversal, port forwarding, or relay server dependencies.

4. Cost Efficiency
This model eliminates the need for:
- Dedicated servers to host the game’s server build.
- Relay or matchmaking servers that would be necessary in a Peer-to-Peer setup.
As a result, it reduces hosting and maintenance costs significantly.
