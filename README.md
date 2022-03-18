# Robotic-Packing-Station-Simulation
Control Theory project, which aim is to create robotic station simulation process without deadlock.
Libraries used for project:
* statemachine - to create state machine
* networkx and matplotlib - visualizing graph
* numpy - calculation
* robopy - to visualize robot moves in 3D
* sys and argparse - to store arguments from console

Statemachine function in main allows to specify path.
Seach function checking for deadlocks.
Display function shows graph

Program allows to choose between two robots (orion and puma).
All automates are specified in automates package. Generator class and commands package were provided by teacher.
Graph package create graph while simulation simulate station.

Station is divided into four automates:
## Main graph 
main_graph.PNG
\Sigma = {0* 1 0* 1 1*}
* q0 = Waiting for the start button to be pressed
* q1 = Start of the packaging process
* q2 = Start of the pick and place process on production line no. 1
* q3 = Start of the pick and place process on production line no. 2
* q4 = Start the wrapping process
* q5 = Stop the process
* q6 = Display an error message

## Packaging Process Graph
\Sigma  =  {0* 1 0* 1 1 1*}
* q0 = Receive start signal from controller
* q1 = Convey the package with the robot
* q2 = Feeding a carton erector
* q3 = Conveying furniture boards with a robot
* q4 = Start the case sealer
* q5 = Sending a success signal to the controller 
process
* q6 = Error signal sent to controller 
* q7 = Transition to wait for the restart button to be pressed

## Production Line Graph
\Sigma  = {0* 1 0* 1 1 1*}
* q0 = Receive start signal from controller 
* q1 = Transfer the package on the production line with the robot
* q2 = Start the production line
* q3 = Sensor reading (product presence check)
* q4 = Sending a success signal to the controller 
process
* q5 = Sending a missing-product/error signal to the controller 
* q6 = Transition to wait for the restart button to be pressed

## Robot Graph
\Sigma  = {0* 1 0* 1 1*}
* q0 = Waiting for start signal from controller
* q1 = Starting the robot
* q2 = Driving the robot tip toward the object
* q3 = Activate the Suction Cup
* q4 = Move the object to a new location
* q5 = Turn off the squeegee
* q6 = Sending a success signal to the controller 
process
* q7 = Sending an error signal to the controller 
* q8 = Entering the waiting mode for the restart button to be pressed
