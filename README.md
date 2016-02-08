# 16745-Assignment-1

## Part 1
I used Matlab's fmincon to do the optimization, providing the joint limits as upper and lower bounds on the parameters and satisfying other constraints throught the cost function. The cost function I used consisted of the distance from the end effector to the target location, the distance between the target quaternion and the end effector quaternion based on the length of the geodesic between them, and cost functions based on proximity to the obstacles and the joint limits. The cost function for the joint limits is 1 divided by the distance between the actual joint value and the limit, summed over each limit. The cost function for the obstacles is the similar, where the distance used is the shortest distance between the obstacle and the robot. These cost functions work well because they fade to 0 at a reasonable distance away from the obstacle or joint limit, but near the constraint they quickly rise to infinity, so there can never be a situation where a local minimum sits on or behind the boundary. They are also relatively easy to differentiate, which helped with the next part.

## Part 2
For this part, I took the gradient of the cost function by hand to pass into the optimization routines.

## Part 3

## Part 4
To find multiple minima, I ran the optimization algorith multiple times with different random starting points each iteration. Also, to avoid running into the same minimum, I added a term to the cost function penalizing points in parameter space that were too close to any previous solution. The point of this was to "fill in" the minimum as much as possible to force the optimizer to explore other regions of parameter space.
