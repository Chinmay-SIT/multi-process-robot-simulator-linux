# multi-process-robot-simulator-linux
This project simulates a multi-robot coordination system using multi-processing, shared memory, and semaphores in C language on Linux. Successfully implemented and tested on a Raspberry Pi running Linux OS.

## Abstract
This project implements a multi-process mobile robot simulation using inter-process
communication (IPC) in C. The robots move on a shared 30x30 grid while avoiding collisions with
each other and reaching designated target points. The robots' movement is synchronized using
semaphores, and their positions are stored in shared memory to allow concurrent access by multiple
processes. The system models a simple yet effective robot coordination algorithm for real-time
operations.

## 1. Introduction
The simulation of multi-process robot systems is an essential aspect of modern robotics,
providing valuable insights into autonomous navigation, coordination, and task execution in
dynamic environments. This project focuses on the development of a multi-robot system where
several robots are tasked with navigating a shared 30x30 grid, with each robot aiming to reach a
predefined target position while avoiding collisions with others. The system utilizes semaphores for
synchronizing the robot processes, ensuring that each robot accesses the shared memory in a
controlled and sequential manner to prevent data conflicts. Collision avoidance is a central feature
of the system, where robots detect and react to nearby robots, adjusting their movement strategies to
prevent overlapping paths.
The project aims to replicate real-world challenges faced by autonomous robots in multi-
agent environments, where interactions with other robots must be managed efficiently to avoid
conflicts and optimize task performance. By employing a simple movement algorithm and
implementing safety protocols like maintaining a minimum distance between robots, the system
ensures that robots can successfully reach their targets without interference. This simulation serves
as a proof of concept for autonomous navigation in controlled environments, and lays the
groundwork for incorporating more advanced techniques such as real-time decision-making,
adaptive pathfinding algorithms, and more sophisticated collision avoidance strategies.
Additionally, this work contributes to the broader field of multi-agent systems and robotics, with
potential applications in areas like warehouse automation, autonomous vehicles, and collaborative
robotics.
