# LearningToFly

This project is my attempt of using reinforcement learning algorithm (TD3) for low level control in quadrotor.

https://user-images.githubusercontent.com/70597091/174797557-82fa398e-896c-4d61-88a0-3b7ce3b0f661.mp4

# Overview

The problem of quadrotor control is classically been solved using control algorithms like MPC for a high level control along with PID for a low level control. However, this whole setup could potentially be replaced by a single system like Neural Network. This projects attempts to do the same.

In this project whole MPC and PID setup is replaced by a 3 layer neural network containing 400, 300 and 4 (in actor) /1 (in critic). The actor networks takes in states (X_diff,Y_diff,Z_diff, V_x, V_y, V_z, W_x, W_y, W_z, Rotation_Matrix) and output actions (a0, a1, a2, a3). The two critic networks takes in (state + action) to tell how good an action is when taken in that state. 

#### States

X_diff,Y_diff,Z_diff are difference between drone position and target position in 3D space.

Rotation Matrix is obtained from roll (R), pitch (P) and yaw (Y) angles.

V_x, V_y, V_z are translational velocities of drone. 

W_x, W_y, W_z are angular velocities of drone.
 
#### Actions

a0, a1, a2, a3 are normalized motor speeds (in [-1, 1]).


#### Reward Function
        
reward = 2.0 -  1.0 * L2_norm(X_diff, Y_diff, Z_diff) - 0.04 * L2_norm(V_x, V_y, V_z)  -0.02 * L2_norm(R,P,Y) - 0.02 * L2_norm(a0, a1, a2, a3) - 0.001 * L2_norm(derivative(a0, a1, a2, a3))

# Requirements

1) Python
2) Jupyter Notebook (Optional)
3) Tensorflow
4) Numpy
5) OpenAI Gym
6) gym-pybullet-drones

Note: Each library must be compatible with others libraries to be installed.

# Trying Out

After installing the dependencies you can either train the agent yourself or test my results. Keep all the files in the same folder. Open the file named ```DroneTD3``` on jupyter notebook and run the all the cells before training cell. You can test my results by running all cell below training cell.
