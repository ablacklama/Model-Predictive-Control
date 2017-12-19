# REFLECTIONS

## The model
It takes a cars state, and desired path and predicts the best control inputs to achieve that path. 
This is done using an optimiser that tries to minimize the cost of the expected path by tuning the control inputs.
I set uper and lower bounds on the variables to make sure the model doesn't output signals that the car can't comply with.
This means the steering is limited to 25 degrees in either direction and the acceleration/braking is between -1 and 1.
We also limit the state variables to be the expected state of the car. And then we evaluate the model.

The cost of the model determains what it cars about. It tries to minimize the cost and some elements that add to the cost, do so in much bigger ways than others.
I choose to multiply my difference in steering angle cost by 50,000 to make sure it didn't swerve. This also helped prevent the negative effects of the time delay.
i multiplied the cte and heading error by 1000 which seemed to be enough to keep the car on track in the right direction.
And the steering angle and acceleration i multiplied by 50. I left the difference in acceleration and the velocity costs low.

## The Time Steps
My N and dt values were choosen by experimentation. 
N seemed to produce the best results aroud 10. 20 caused too much lag and but my computer handled 10 just fine.
dt was determained by the N value. I wanted the model to look at least 1 second into the future so i choose a dt value of .1
