# Unix-Buffer-Cache-Simulation
  Simulation of Unix's Buffer Cache.  This Simulation is implemented in Python. This serves as a tool to give some insight into how Buffer Cache in Unix Operating System handles all the Process requests for read/write operations.
  
## Prerequisite
  * Python
  * Linux / Unix Terminal (Some Terminals don't support the escape codes for colours, and may output poorly formated results)
  
## How to Run?
  Simply run the `main.py` file using the command `> python main.py`.
  
## What it does?
  This is a simple command-line Simulation of Unix's Buffer Cache Management System. Using this you can simulate the scenarios which can occur while handling the read/write requests of different processes in a Unix System.

## What is Buffer Cache?
  Buffer Cache is a fast memory which OS uses to perform the read/write operations much quicker than reading/writing directly from the secondary storage devices (which is comparatively slower). It maintains several buffers of some predefined sizes and uses them to store data which gets read from/written to secondary storage devices and allocates these buffers to Processes requesting to read data from storage.

## Getblk Algorithm
  Buffer Cache uses `getblk` algorithm to handle allocation of buffers to processes.
  
  ![Buffer Cache Algo](/imgs/0.getblk_algo.jpg)

  There are 5 different Scenarios which you can encounter in the `getblk` algorithm, namely : 
  1. Block in the hash queue, and its buffer is free.
  2. Cannot find a block on the hash queue => allocate a buffer from the free list.
  3. Cannot find a block on the hash queue => allocate a buffer from the free list but buffer on the free list marked “delayed write” => flush “delayed write” buffer and allocate another buffer.
  4. Cannot find a block on the hash queue and free list of the buffer is also empty.
  5. Block in the hash queue, but the buffer is busy.
  All of these 5 scenarios with their corresponding Hash Tables are shown in the [Scenarios](/imgs/Scenarios) folder.

## UI
  Following are a few of the snapshots of the user interface for this tool. You can find more snapshots in the [imgs](/imgs) folder.
  
  #### Main Menu
  ![Main Menu](/imgs/1.%20Main%20Menu.png)
  
  #### Hash Queue
  ![Hash Queue](/imgs/2.%20Hash%20Queue.png)
  
  #### Reading a Block
  ![Reading a Block](/imgs/6.Reading%20a%20Block.png)
  
 ### UML Diagram for the Project
  [UML Diagram.pdf](/imgs/UML.pdf)
