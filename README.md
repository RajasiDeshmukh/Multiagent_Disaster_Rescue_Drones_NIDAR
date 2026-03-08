# Multiagent_Disaster_Rescue_Drones_NIDAR

> ⚠️ Note: This repository contains selected modules of a larger UAV perception and geotagging pipeline developed for the NIDAR competition. Some components are withheld due to an ongoing research publication.

## Abstract

Flood-affected environments impose significant constraints on rapid human localization and relief delivery due to damaged infrastructure, dynamic terrain, and limited situational awareness. This work presents a fully autonomous multi-drone system for real-time human detection, geolocation, and targeted parcel delivery in flood disaster scenarios.

The proposed system integrates systematic area coverage, onboard deep-learning-based perception, and dynamic mission execution. The affected region is partitioned equally among multiple drones, each executing a lawnmower-based coverage pattern to ensure complete and non-overlapping exploration. A custom-trained aerial human detection model processes live video streams onboard, producing pixel-level detections that are transformed into real-world metric offsets through camera projection and drone attitude estimation, and subsequently converted into GPS coordinates.

To ensure robustness and eliminate redundant responses, detections are subjected to geofence validation, distance-based clustering, and persistence filtering, preventing repeated actions on the same individual. Verified detections are logged by storing annotated images, full mission video, and geolocated detection points in a shared data interface accessible by the mission controller. Upon confirmation, the drone autonomously transitions from AUTO to GUIDED mode, deviates from the preplanned coverage path, navigates to the detected location, performs a stabilized hover, and executes servo-actuated parcel deployment, before resuming autonomous coverage.

Multi-drone coordination is implemented through a dynamic role-based execution model in which each drone operates either as a Scout or an Executor, with roles determined in real time based on payload availability and mission state. A drone that has exhausted its onboard payload while still having unvisited coverage strips remaining continues operation in Scout mode, prioritizing area exploration and human detection without performing parcel delivery. In this mode, all verified human detection coordinates are logged and transmitted to peer drones capable of executing delivery actions.

If a Scout drone completes its assigned coverage region and other drones retain uncompleted strips, it may dynamically accept additional coverage strips through a Donor–Acceptor strip exchange mechanism, enabling continued exploration without idle time. Conversely, a drone operating in Executor mode, i.e., with available payloads, may receive detection coordinates from Scout drones and autonomously navigate to those locations to perform targeted parcel delivery, independent of which drone originally detected the human.

Mission state, detection metadata, and strip completion status are exchanged periodically and upon completion of each coverage strip, allowing consistent situational awareness and coordinated task allocation across the fleet. This cooperative strategy decouples detection and delivery responsibilities, ensuring efficient utilization of aerial resources, minimizing redundant coverage, and enabling scalable, fault-tolerant multi-drone disaster response operations.

The proposed system demonstrates a scalable and reliable framework for autonomous human detection and targeted relief delivery in flood disaster scenarios.


https://github.com/user-attachments/assets/9368470e-f5fe-4581-965b-b93d9443f2f3

<img width="823" height="490" alt="Screenshot 2026-01-17 024821" src="https://github.com/user-attachments/assets/6bc105c1-4dec-4777-bd76-71fe88823920" />
<img width="871" height="447" alt="Screenshot 2026-01-17 024953" src="https://github.com/user-attachments/assets/a3501607-9ed3-4314-9410-48c5aaf5bcd4" />
<img width="298" height="505" alt="Screenshot 2026-01-17 025151" src="https://github.com/user-attachments/assets/35ad5f8b-fc13-40a1-9a2f-7735d8cac502" />

<img width="913" height="492" alt="Screenshot 2026-01-17 025423" src="https://github.com/user-attachments/assets/dd0816de-685c-43f6-bbc8-9e24275e9d7d" />


