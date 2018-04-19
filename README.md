### Objective
The objective of this project is to create a PID (Propotional-Integral-Derivative) controller to navigate a car in simulator. Basic goal is to tune PID parameters so as to produce steering in such a way that car stays within track and as close as possible to reference trajectory.

## Result
Final project video can be found [here](https://www.youtube.com/watch?v=WhzDx4OTRs4)

## PID Components
### Proportional Component 
**P component** steers the car proportional to CTE (Cross Track Error). CTE is deviation of the car from the reference trajectory. If the car is towards left of the reference trajectory it tries to steer towards the right or vice versa. In this process car overshoots but then eventually gets back forming oscillations. The more the CTE, more effect it will have on correction. P value should be minimum possible to reduce the oscillation effect.
### Integral component
**I component** is sum of all CTE (Cross Track Error) and will reduce the CTE by encountering the bias in it. The more the CTE the more effect it will have on correction. 

### Derivative component
**D component** is rate of change of CTE. It will remove the oscillations produced by P component.

## Parameter Tuning
There are few key aspects that needs to be considered in process of tuning PID parameters:
* Rise time – the time it takes to get from the beginning point to the target point
* Overshoot – the amount that is changed too much; the value further than the error
* Settling time – the time it takes to settle back down when encountering a change
* Steady-state error – the error at the equilibrium
* Stability – the “smoothness” of the speed

I approached this project with ***manual tuning of PID parameters***. For this I initially set Kp, Ki, and Kd to 0. I then Increased Kp, but this eventually produced overshoots. I then increased Kd to encounter overshoots. Then finally increased Ki so as to remove any remaining CTE. I had to go over quite a bit of iterations but was finally able to reach to following set of values:-
```
P - 0.2
I - 0.00004
D - 5.0
```

### Additional Note:
Due to hardware limitations, I had to proceed with lower values of throttle rate of 0.4. Any throttle rate more than this leads car out of track as processing capabilities are too limited for such a throttle rate.

