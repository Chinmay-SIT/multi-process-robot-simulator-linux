# Multi-Process-Robot-Simulator-Linux
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

## 2. System Design
• Overall Architecture: The system architecture includes the following components:
• Shared Memory: Used to store robot positions and other relevant state information.
It allows multiple robot processes to access and update the data.
• Semaphores: Used for synchronizing access to the shared memory to ensure that
robots do not overwrite each other’s data simultaneously.
• Robot Processes: Each robot is modeled as a separate child process. These processes
update the robot's position and check for collisions with other robots.
• Grid Display: The grid is displayed in the terminal with robot positions shown in
real-time.
• Data Structures:• Robot Structure: Contains the robot’s ID, current position (x, y), target position,
speed, and active status.

![IMG_20250428_143123578_HDR](https://github.com/user-attachments/assets/92fa22a4-1e01-4be7-b348-57c770213c71)


## 3. Implementation
• Robot Movement Algorithm:
• Each robot moves towards its target position using basic movement logic (up, down,
left, right).
• Robots avoid collisions by checking the distance to other robots before moving. If
another robot is too close, the robot attempts to find an alternate safe direction.
• If no safe direction is found, the robot pauses and retries later.
• Inter-Process Communication (IPC):
• Shared memory is used to store the robot positions and state information, allowing
each robot process to access the data concurrently.
• Semaphores are used to ensure mutual exclusion when accessing and modifying
shared memory, preventing race conditions.
• Collision Detection:
• Robots calculate the Euclidean distance between themselves and other robots before
moving. If the distance is below a predefined threshold (SAFE_DISTANCE), a
collision is detected.
• If a robot encounters a collision, it tries to back off or find an alternate safe path by
checking available movement options (up, down, left, right).
• Simulation Flow:
• The program initializes the robots, assigns random start and target positions, and
creates child processes for each robot.
• The robots continuously move towards their target positions, update the grid display,
and check for collisions. The simulation ends when all robots reach their targets.

## 4. Results and Discussion
The simulation of the multi-process robot system was successfully implemented, and the
robots were able to navigate the grid while avoiding collisions with one another. Each robot, upon
starting, was assigned a target position on the grid, and they moved towards their targets in a
coordinated manner. The robots communicated indirectly via semaphores to prevent race conditions
when accessing the shared memory, ensuring that only one robot could update its position at a time.
The robots utilized a simple movement strategy, where they calculated the direction towards their
target and moved one step at a time. In case of a potential collision with another robot, the system
checked the distance between them. If the robots were too close, the moving robot either paused for
a brief moment or attempted an alternate route to avoid the collision. The system performed well in
situations where multiple robots had to navigate the grid simultaneously, adjusting their paths
dynamically to prevent interference. The simulation also included a delay between movements to
simulate smooth motion, enhancing the realism of the process. The robots reached their targets
successfully without significant issues, and the simulation ran as expected with minimal collisions,
which were handled effectively. The overall performance of the system demonstrated the potential
of multi-process coordination and collision avoidance in dynamic environments.
The positions of the robots are displayed, indicating that they navigated the
grid and completed their tasks. This output reflects the success of the simulation, confirming thatthe robots were able to reach their targets without issues. Although there is no graphical
representation, the textual output clearly shows the final positions of the robots, demonstrating the
effectiveness of the implemented collision avoidance and movement strategies. This result
highlights the potential for real-world applications where robots need to operate in a shared
environment with limited space, successfully completing their tasks without interference.

## 4. Challenges
During the development and simulation of the multi-process robot system, several
challenges were encountered. One of the primary challenges was ensuring that the robots moved
efficiently without colliding, while simultaneously avoiding deadlock situations. The system's
collision avoidance mechanism, which involves checking distances between robots and adjusting
their paths, required careful coordination to ensure that robots could dynamically adjust their
movements when blocked by others. Another challenge was maintaining synchronization between
the processes, as each robot operated in its own child process. This required effective use of
semaphores to control access to the shared memory, preventing race conditions and ensuring that
only one robot updated its position at a time. Moreover, implementing a smooth and realistic
simulation of robot movement, with appropriate delays to mimic real-world motion, was another
challenge that required fine-tuning to prevent the robots from moving too quickly or unrealistically.
Additionally, as the number of robots or complexity of the grid increased, the system’s performance
could be impacted, especially if the robots were forced to perform multiple backtracking maneuvers
in tight spaces.

• Ensuring smooth multi-process synchronization to avoid race conditions and ensure correct
data sharing.

• Fine-tuning the collision avoidance and movement strategy to prevent inefficient
backtracking and improve robot coordination.

Future improvements could involve refining the collision avoidance logic and exploring more
sophisticated pathfinding algorithms to reduce movement inefficiencies in complex scenarios.

## 5. Conclusion
In conclusion, the multi-process robot simulation demonstrated effective coordination and
collision avoidance within a shared environment. By utilizing semaphores for process
synchronization and shared memory for robot state management, the system ensured that each robot
could navigate towards its target without interference. The collision avoidance strategy worked well
under simple conditions, successfully preventing direct collisions and allowing robots to find
alternative paths when blocked. While the basic framework achieved the desired objectives, the
system could be further optimized by integrating more advanced path finding algorithms and
enhancing the decision-making process to improve efficiency, especially in more complex
scenarios. Overall, the project provided valuable insights into the challenges of multi-process
coordination and real-time collision avoidance in a dynamic environment, with potential
applications in areas like autonomous robotics and multi-agent systems.
