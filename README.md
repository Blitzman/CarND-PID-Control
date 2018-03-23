# PID Controller Project

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
Self-Driving Car Engineer Nanodegree Program

## Requirements

* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* Udacity Simulator [Download link](https://github.com/udacity/self-driving-car-sim/releases)


Tips for setting up the environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d).

## Compilation and Execution

1. Clone this repo
2. cd to repo root dir.
3. `mkdir build`
4. `cd build`
5. `cmake ..`
6. `make`
7. `./pid`
8. Run simulator

## Rubric

### Compiling

#### Your code should compile

Code compiles by issuing `mkdir build`, `cd build`, `cmake`, and `make` without errors. The provided `CMakeLists.txt` was not modified.

### Implementation

#### The PID procedure follows what was taught in the lessons

The PID controller implementation can be found in `src/PID.cpp`. That source file implements the `PID::Init`, `PID::UpdateError` and `PID:TotalError` as described in the lessons. The first one just initializes coefficients and variables for the controller whilst the second one computes proportional (P), integral (I), and derivative (D) errors which are then multiplied by the appropriate coefficients in the third method to compute the final controller error.

### Reflection

#### Describe the effect each of the P, I, D components had in your implementation

* The proportional (P) component is the main one whose goal is to steer the car against the cross-track error (i.e., towards the lane center). Only adding this component causes the car to overshoot the lane center.
* The integral (I) component's goal is to eliminate a systematic error that might be introduced by a biased controlled system. This is not the case of the simulator. Only adding this component causes the car to drive in circles since there is no bias to correct.
* The derivative or differential (D) component's objective is to avoid the overshooting caused by P by smoothing its approach to the lane center (i.e., smooth the error minimization process and damp oscillations). 

#### Describe how the final hyperparameters were chosen

### The vehicle must successfully drive a lap around the track

#### No tire may leave the drivable portion of the track surface. The car may not pop up onto ledges or roll over any surfaces that would otherwise be considered unsafe (if humans were in the vehicle)

With the aforementioned implementation and parameter settings, the car is able to complete laps in the circuit without leaving the drivable portion of the track surface. The PID controller in action can be checked in the following video:

[![ProjectVideo](http://img.youtube.com/vi/46Wz3tHqwPY/0.jpg)](https://www.youtube.com/watch?v=46Wz3tHqwPY "Self-Driving Car Nanodegree - PID Controller")
