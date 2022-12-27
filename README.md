# Capstone-Project---Strange-Attractors
Abstract
We created interactive simulations and animations of the Lorenz, Rossler, and Henon attracors by solving their differential equations using Euler's and Modified Euler's method. We then compared the extent of the "butterfly effect" and noted that changes of <0.5 do not yield significant changes in the resulting figures. We also examined the 5-line fractal structure of the Henon attractor. An in-depth paper is attached which includes more ddetails about our project.

Introduction
This project was inspired due to strange attractors’ abundant applications in modern physics and mathematics. There is a strange attractor in every chaotic system [1]. Therefore, increasing our understanding of strange attractor behavior would further our understanding of chaotic systems, such as chaotic nonlinear oscillators. Additionally, strange attractors are the link between chaos theory and fractals.

The plots show the fractal behavior in the henon attractor, as we can see the similar five-line pattern every time we zoom into the red box. The reason why the plots look faint is because there are only 10,000 data points plotted. The more data points plotted, the clearer the fractals are.

To collect the data points necessary to plot the Lorenz attractor, one must first solve the differential equations shown in 
dx/dt = P(y − x) dy/dt = Rx−y−xz dz/dt = xy − Bz
For the Lorenz attractor, the initial conditions are x = 0, y = 1, z = 0, and the constants P, R, and B, are equal to 10, 28, and 8/3 respectively. These are the values used by Edward Lorenz himself [2]. However, through experimentation, differences in the constants of up to 2 yield no noticeable changes.

In order to solve the differential equations, we use Euler’s method. The process goes like this: We solve for the instantaneous slope for each dimension at each position by plugging the previous x, y, and z values into the differential equations. Next, we multiply the calculated slope by dt, which we have set as 0.01. This results in the change in x, y, or z. Adding this value to the previous x, y, or z value gives us the next value, which we can then append to our data set. After 10,000 iterations of this process, we have a full data set, which we can then plot to get the result in Figure 3.

Rossler Attractor
Like the Lorenz attractor, one must solve the Ro ̈ssler attractor’s ordinary differential equations to plot it, so the process to fill the data set and plot the attractor is similar.
dx/dt = −(y + z) dy/dt = x + Ay dz/dt = B+xz−Cz
We use a new set of three differential equations (Figure 4) to plot the attractor. The constants A, B, and C are equal to 0.2, 0.2, and 5.7 respectively. Using Euler’s method, which is described in the previous section, we get the 3-D plot of the Ro ̈ssler attractor shown below.

Henon Attractor
Unlike the Lorenz and Ro ̈ssler Equation, the equations of the Henon attractor(Figure 6) are not differential equa- tions, so they need a method other than Euler’s method in order to be solved.
yn+1 = 0.3xn
Instead, we use recursive functions to solve the equations. Starting with the initial conditions of 0 for both x and y, we take every x and y and plug them into the equations of Figure 6 to get the next x and y values. If we repeat this process with a for loop 10,000 times, we get a data set which we can then plot to get Figure 7.
 Fig. 7. Henon Attractor Plotted in 2-Dimensions
Unlike the Lorenz and Ro ̈ssler attractor, the Henon attractor’s path is 2-Dimensional because it only has two variables.

Animation
2-Dimensional Animation
By importing matplotlib.animation, we used the writers[’ffmpeg’] feature to render the frames of our animation. Next we created a marker, a red circle, which represented our attractor’s position for each of the 10,000 data points. With a for loop, we set the red circle’s position at each of the points of our data set and added each frame to our animation with grabframe. We created 2-D animations of all three attractors using this method. Figure 8 shows a snapshot of the 2-D Lorenz animation.

Because writers[’ffmpeg’] only accepts two-dimensional data, we were unable to create three-dimensional anima- tions with this method, which leads us to our next step.

3-Dimensional Animation
To make a 3-Dimensional Animation, we imported FuncAnimation from the matplot.lib.animation library. Next, we defined a function that took in our three-dimensional data sets and set the animation’s graph to a three- dimensional graph. Afterward, we wrapped our data set into a numpy array in preparation to be passed into FuncAnimation. We also created a starting point for animation using plt.plot and passed in our initial x, y, and z positions from the array. Finally, the function, array of our data, and the initial value into the parameters of FuncAnimation. FuncAnimation iterates through each value of the data set and generates a three-dimensional an- imation. We created 3-D animations for the Lorenz and Ro ̈ssler attractors using this method. Figure 9 shows a snapshot of the Ro ̈ssler attractor being made.
Fig. 9. 3-Dimensional animation of the Ro ̈ssler attractor in progress

Extensions
Interactive Plots
An idea proposed by Professor Jazaeri was to make our plots interactive. To accomplish this, we imported ipympl. We also transformed each of our graphs into subplots instead of regular plots, as this is a prerequisite for ipympl. Once made interactive, plots can be dragged around, rotated, and zoomed-in or zoomed-out. By hovering your cursor over a point, ipympl also displays the coordinates of your cursor’s position.

Comparing ODE Solving Methods
Another extension to our project was to compare Euler’s and Modified Euler’s method of solving ordinary differ- ential equations. For the Modified Euler’s we take the average of both the previous point’s slope as well as the next point’s slope instead of just the previous slope. We get the next slope value by first creating a prediction with Euler’s method. This process is called the predictor-corrector method. The average slope is then multiplied by dt to get the change in x, y, or z, and then appended to the previous value to get the next. Modified Euler’s method is more accurate than Euler’s method. We plotted the Lorenz attractor once using Euler’s method and once using Modified Euler’s method to fill its data set. The results are shown in Figure 11.

Euler and Modified Euler Lorenz attractor plots
Intrigued by the noticeable differences between the two plots, we plotted the differences in values of the Euler’s and Modified Euler’s methods. We believe the reason why the differences in values reach up to the high thirties is because a minor change in values in the beginning of the plotting process ends up leading to vast changes later on, a trait unique to strange attractors. It is also interesting to note that the differences in values appear to follow the same trend across all three dimensions’ values.

The final output of our project includes interactive 2-Dimensional and 3-Dimensional plots and animations of the Lorenz, Ro ̈ssler, and Henon attractors. It also includes a comparison of plots solved using Euler’s and Mod- ified Euler’s method. Creating and coding the algorithm to plot each of the attractors went surprisingly smooth. However, it was the animation aspect that proved difficult. We learned animation and Modified Euler’s method from scratch and spent much more time debugging our code than expected. Installing and importing ipympl for interactivity also proved challenging, as it created an implementation error that was difficult to solve. However, after hours of trial and error, all of these problems were eventually resolved. Overall, this project was extremely rewarding. It served as both an excellent way to test out the skills we learned in class and as a great way to dig into and experiment with a subject on the frontier of physics research. I aim to expand this project in the near future by plotting even more complex strange attractors and experimenting with a variety of initial conditions.
