# PID Control Project
Self-Driving Car Engineer Nanodegree Program

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

In this project, we build a PID Controller to provide steering directions to a vehicle in the simulator.


This project involves the Term 2 Simulator which can be downloaded [here](https://github.com/udacity/self-driving-car-sim/releases)


For instructions on how to run or build this project, refer to the [Instructions here](./Instructions.md)


The detailed evaluation of this project can be found [here](https://review.udacity.com/#!/rubrics/1972/view).
-----

## Reflection
The objective of the PID controller build for this project was to correct the steering direction of a vehicle based on it's deviation from the desired track.

The PID controller is comprised of 3 parameters with different effects on the movement of the vehicle.

### 1. Proportional (P):
The proportional parameter in the controller determines to which extent should the direction change respective to the cross-track-error (CTE). Given the direct relationship, it has the potential for agressive behaviour if the parameter is set too high.

After manual tunning, I selected the value of 0.11. Any range between 0.11 and 0.2 worked fine, but I observed a lot more overshooting as I increased the value.

## 2. Integral
The integral parameter in the controller adjusts in proportion to the running sum of cross-track-error during all iterations. It's purpose is to ensure that the CTE is decreasing in the long term and stabilizes.

After manual tunning, I selected the value of 0.0001. We have to be specially careful with this parameter as it is the fastest increasing. 


## 3. Differential (D):
The differential parameter in the controller adjusts in proportion to changes in CTE. Given that the rate of change is smaller than the error after the initial iteration, this parameter is a lot more useful in decreasing oscillations.

After manual tunning, I selected the value of 4.0. Since this is intending to reduce the rate of change, it has to be setup a lot more aggresively (magnitude will decrease significanlty as CTE decreases between iterations).

## Cross-TRack-Error
In order to calculate cross-track-error, I used the following equation:

CTE = - Kp * CTE - Kd * (CTE - CTE@t-1) - Ki * (Σ CTE)
CTE = - Kp * p_error - Kd * d_error - Ki * i_error


 
