# Robotic Assembly Simulation in RobotStudio

This repository presents a robotic assembly project developed in the context of CNC systems and flexible automation. The project combines mechanical part design, CNC manufacturing, custom gripper-finger development, and ABB RobotStudio simulation with RAPID programming for an automated two-part assembly process.

## Project Overview

The objective of the project is to simulate and validate an automated assembly sequence in which two components are joined into a single functional unit.

The process consists of:

- picking the **base** from a conveyor belt
- transferring it to the assembly position
- picking the **guide** from a fixed location
- inserting the guide into the previously positioned base

The assembly task is performed in the **ABB RobotStudio** environment and later verified in laboratory conditions on a real ABB robot.

## Main Components of the Project

This project includes the following stages:

- mechanical design of the parts
- design of custom robot gripper fingers
- CNC manufacturing of the base and guide
- 3D printing of the fingers
- G-code generation in SolidCam
- robotic simulation in RobotStudio
- RAPID programming of the assembly sequence
- laboratory validation of the solution

## Part Design

Three key components were designed:

- **base**
- **guide**
- **robot fingers**

The parts were modeled in **SolidWorks**. The base and guide were designed to allow precise alignment during assembly, while the fingers were designed according to the gripping requirements of each object.

### Grasping logic
- The **base** is grasped using an **external grip**
- The **guide** is grasped using an **internal grip**

This distinction is essential because the two parts have different geometries and require different contact strategies for stable handling.

## Manufacturing

The project includes actual manufacturing of the designed components:

- the **base** was produced on a **CNC milling machine**
- the **guide** was produced on a **CNC lathe**
- the **fingers** were fabricated by **3D printing**

The machining process was prepared in **SolidCam**, where the corresponding machining strategies and G-code were generated.

## Simulation in RobotStudio

The robotic workcell was modeled in **ABB RobotStudio** and includes:

- an industrial ABB robot
- a conveyor belt
- a fixed pick position for the guide
- an assembly position for joining the parts

The simulation was used to verify:

- collision-free operation
- correct motion sequence
- proper grasping logic
- feasible assembly trajectory
- consistency between designed geometry and robotic execution

## Motion Sequence

The robot executes the following sequence:

1. waits for the base to arrive on the conveyor
2. stops the conveyor through ABB–PLC communication
3. picks the base from the conveyor belt
4. places the base at the assembly location
5. moves to the fixed pick location
6. picks the guide
7. inserts the guide into the base
8. returns to the home position

Intermediate approach points are used to improve safety and reduce collision risk during grasping and insertion.

## RAPID Programming

The assembly process is programmed in **RAPID** and includes:

- initialization of digital outputs
- ABB–PLC communication
- separate motion procedures for the base and guide
- use of `MoveJ` and `MoveL` instructions
- gripper actuation through digital outputs
- synchronization through wait commands

The implemented logic separates the operation into two main procedures:

- base transfer path
- guide transfer and insertion path

## Practical Issue and Adjustment

During implementation, one practical issue was identified: the robot risked colliding with the table while picking the guide.

This problem was solved by:

- physically elevating the guide in the laboratory setup
- raising the corresponding work object in the simulation

This adjustment ensured safe and feasible motion both in simulation and in real execution.

## Results

The project confirmed that the designed system can successfully perform the intended assembly task.

The results show that:

- the manufactured parts were geometrically suitable for assembly
- the custom fingers enabled reliable grasping of both components
- the RobotStudio simulation correctly represented the task
- the final robotic sequence was executable in laboratory conditions

The project demonstrates a complete workflow from CAD modeling and manufacturing to robotic simulation and practical validation.

## Tools and Technologies

- SolidWorks
- SolidCam
- CNC milling
- CNC turning
- 3D printing
- ABB RobotStudio
- RAPID programming

## Suggested Repository Structure

```text
.
├── README.md
├── reports/
│   └── CNC_RobotStudio_Assembly_Project_Report.pdf
├── robotstudio/
│   └── assembly_sequence.mod
├── images/
│   ├── base_model.png
│   ├── guide_model.png
│   ├── finger_model.png
│   ├── workcell_robotstudio.png
│   └── abb_robot_setup.png
└── media/
    └── demo_link.txt# robotstudio-cnc-assembly-simulation
Robotic assembly project combining CNC-manufactured parts, custom gripper-finger design, and ABB RobotStudio simulation with RAPID programming for pick-and-place assembly.
