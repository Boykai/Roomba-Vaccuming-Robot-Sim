# Roomba-Vaccuming-Robot-Sim
### MITx 6.00.2x - Roomba Vaccuming Robot Simulation
#### By James Tooles


## Simulation Overview
iRobot is a company (started by MIT alumni and faculty) that sells the Roomba vacuuming robot (watch one of the product videos to see these robots in action). Roomba robots move around the floor, cleaning the area they pass over.

In this problem set, you will code a simulation to compare how much time a group of Roomba-like robots will take to clean the floor of a room using two different strategies.

## Simulation Details
Here are additional details about the simulation model. Read these carefully.

* Multiple robots
In general, there are N > 0 robots in the room, where N is given. For simplicity, assume that robots are points and can pass through each other or occupy the same point without interfering.

* The room
The room is rectangular with some integer width w and height h, which are given. Initially the entire floor is dirty. A robot cannot pass through the walls of the room. A robot may not move to a point outside the room.

* Tiles
You will need to keep track of which parts of the floor have been cleaned by the robot(s). We will divide the area of the room into 1x1 tiles (there will be w * h such tiles). When a robot's location is anywhere in a tile, we will consider the entire tile to be cleaned (as in the pictures above). By convention, we will refer to the tiles using ordered pairs of integers: (0, 0), (0, 1), ..., (0, h-1), (1, 0), (1, 1), ..., (w-1, h-1).

* Robot motion rules
 * Each robot has a position inside the room. We'll represent the position using coordinates (x, y) which are floats satisfying 0 ≤ x < w and 0 ≤ y < h. In our program we'll use instances of the Position class to store these coordinates.
 * A robot has a direction of motion. We'll represent the direction using an integer d satisfying 0 ≤ d < 360, which gives an angle in degrees.
 * All robots move at the same speed s, a float, which is given and is constant throughout the simulation. Every time-step, a robot moves in its direction of motion by s units.
 * If a robot detects that it will hit the wall within the time-step, that time step is instead spent picking a new direction at random. The robot will attempt to move in that direction on the next time step, until it reaches another wall.

* Termination
The simulation ends when a specified fraction of the tiles in the room have been cleaned.

### RectangularRoom Class
You will need to design two classes to keep track of which parts of the room have been cleaned as well as the position and direction of each robot.

In ps2.py, we've provided skeletons for the following two classes, which you will fill in in Problem 1:
* RectangularRoom: Represents the space to be cleaned and keeps track of which tiles have been cleaned.
* Position: We've also provided a complete implementation of this class. It stores the x- and y-coordinates of a robot in a room.

Read ps2.py carefully before starting, so that you understand the provided code and its capabilities.

### Problem 1
In this problem you will implement the RectangularRoom class. For this class, decide what fields you will use and decide how the following operations are to be performed:
* Initializing the object
* Marking an appropriate tile as cleaned when a robot moves to a given position (casting floats to ints - and/or the function math.floor  -may be useful to you here)
* Determining if a given tile has been cleaned
* Determining how many tiles there are in the room
* Determining how many cleaned tiles there are in the room
* Getting a random position in the room
* Determining if a given position is in the room

### Robot Class
In ps2.py we provided you with the Robot class, which stores the position and direction of a robot. For this class, decide what fields you will use and decide how the following operations are to be performed:

Initializing the object
* Accessing the robot's position
* Accessing the robot's direction
* Setting the robot's position
* Setting the robot's direction

Complete the Robot class by implementing its methods in ps2.py.

Note: When a Robot is initialized, it should clean the first tile it is initialized on. Generally the model these Robots will follow is that after a robot lands on a given tile, we will mark the entire tile as clean. This might not make sense if you're thinking about really large tiles, but as we make the size of the tiles smaller and smaller, this does actually become a pretty good approximation.

### StandardRobot Class
Each robot must also have some code that tells it how to move about a room, which will go in a method called updatePositionAndClean.

Ordinarily we would consider putting all the robot's methods in a single class. However, later in this problem set we'll consider robots with alternate movement strategies, to be implemented as different classes with the same interface. These classes will have a different implementation of updatePositionAndClean but are for the most part the same as the original robots. Therefore, we'd like to use inheritance to reduce the amount of duplicated code.

### Running the Simulation
In this problem you will write code that runs a complete robot simulation.

### RandomWalkRobot Class
iRobot is testing out a new robot design. The proposed new robots differ in that they change direction randomly after every time step, rather than just when they run into walls. You have been asked to design a simulation to determine what effect, if any, this change has on room cleaning times.
