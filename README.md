# LearningToFly

This project is my attempt of using reinforcement learning algorithm (TD3) for low level control in quadrotor.

https://user-images.githubusercontent.com/70597091/173548364-736bf826-7975-4cc4-8fe0-2bdb49c0f1b9.mp4

# Overview

The problem of quadrotor control is classically been solved using control theory using control algorithms like MPC for a high level control along with PID for a low level control. However, this whole setup could potentially be replaced by a single system like Neural Network. This projects attempts to do the same.

In this project whole MPC and PID setup is replaced by a 3 layer neural network containing 400, 300 and 4 (in actor) /1 (in critic). The actor networks takes in states (X,Y,Z, R,P,Y, V_x, V_y, V_z, W_x, W_y, W_z, X_d, Y_d, Z_d) and output actions (a0, a1, a2, a3). The two critic networks takes in (state + action) to tell how good an action is when taken in that state. 

#### States

X, Y, Z are drone position in 3D space.

X_d, Y_d, Z_d are target_position in 3D Space.

R, P, Y are roll, pitch and yaw of the drone.

V_x, V_y, V_z are translational velocities of drone. 

W_x, W_y, W_z are angular velocities of drone.
 
#### Actions

a0, a1, a2, a3 are normalized motor speeds (in [-1, 1]).


#### Reward Function


w_pos = 5e-2, w_att = 1e-3,w_act = 1e-4, w_vel = 1e-4 are the weights tells the Neural Network how much importance is given to which factor.
        
reward = relu(0.1 - w_pos * pos_err - w_att * att_err - w_act * act_err - w_vel * vel_err)


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






