## Model 
The vehicle model used in this project is a kinematic bicycle model.

* x,y denote the position of the car
* psi the heading direction
* v its velocity
* cte the cross-track error
* epsi the orientation error
* Lf is the distance between gravity of the vehicle and the front wheels

## Process Steps
1. transform global coordinate to car coordinate
2. calculate poly Coefficients
3. Prepare state Vector and coeff, pass the parameters to solve, 
4. inside MPC solve,  define the Cost Function: Main objective - to minimize our cross track, heading, and velocity errors. 
   find that sometime the car run away from the trajectory,  add more weight to delta constraints to retrain it.
   reduce N from 25 to 10 to avoid the track CTE of far way
5. add 0.1s*2  latency  to actuators
   ```
               int latency=1;
               double steer_value = traj.Delta.at(latency);
               double throttle_value= traj.A.at(latency);
```
    