# CarND-Controls-PID
## Self-Driving Car Engineer Nanodegree Program

---

This project mainly involves implementing PID controller (Proportional-Integral-Differential) and finetune hyperparameters of the PID controller so that the car will drive throgh the drivable area and follow the center of the road. The simulator provides Cross-Track-Error(CTE) depending on which we are deciding the steering angle of the car.

## Discussion about effect of P, I, and D component:
---

* P or Proportional component has most significant and observable effect on the steering angle. It proportionally steers the car in the opposite direction based on CTE that is if the car is left to the center it causes the car to steer right and if it is far left to the center it causes the car to hard steer to the right. However, if we will set P value too high then it will cause the car to oscillate across the road instead of settling at the center and if the P is too low it will take more time to the car to settle at the center. Following video shows the effect of P without I and D.
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/U91_wb3CyaA/0.jpg)](https://youtu.be/U91_wb3CyaA)

* D or Differential component smothen out the oscillations and overshoots caused by P. It is based on the difference between the previous value of CTE and current value of CTE. If the difference is increasing then it will make car to steer more to get to center line. If the difference is decreasing then it will reduce the steer angle so that the car will not overshoot. If the value of D is too high then it will make car to stay at center line but it will not allow car to take turns properly. If the value is too low then it will not counteract on oscillations sufficiently. Following video shows the effect of P with D.
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/Hg8JaTDwmjs/0.jpg)](https://youtu.be/Hg8JaTDwmjs)

* I or Integral component counteract on any bias in movement in the car so that car get to the center of road. It is calculated based on the previous all CTE. If the sum of CTE is large that means for long duration car is not at center of the road then we can see the effect of the I component. If the value of I is chosen too high it will cause car to drift towards other side of center and if chosen too low it will not be sufficient to make car to be aligned at center of the road.

## Parameter Tunning:
---
I tuned parameters for P, I and D manually.

P - 0.18

I - 0.001

D - 3.0

I tuned my parameters as follows:

- To disable Kp, Ki and Kd set Kp, Ki, and Kd to 0.

- Increase Kp gradually so that car can move throgh the track. But it certainly wnet outside the track because of oscillations and overshooting caused by Kp.

- To counteract overshooting increase Kd so that vehicle will move throgh entire track in drivable region.

- Once car is moved through entire track If is not centering properly at curves try increasing Ki values by smaller steps.

## Final Video:
---
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/q3QI054-OeQ/0.jpg)](https://youtu.be/q3QI054-OeQ)