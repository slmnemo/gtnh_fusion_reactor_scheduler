### Main Specification

I am about to hit LuV and want to transition my power to fusion. However, fusion reactors are expensive and time consuming to run! This is a huge problem, as I want to be able to craft things and also use this fusion reactor for power without micromanaging it.

This project seeks to automate multiple tasks using a single fusion reactor through OpenComputers. It will generate power as needed for the base while also scheduling crafts during power generation down-time. 

## Real-Time Operating System

This project is built on the idea of a event-driven Real-Time Operating System (link to wikipedia page https://en.wikipedia.org/wiki/Real-time_operating_system#Design_philosophies). This is chosen to ensure that power demands for a power grid are met even when the fusion reactor is "busy". 

Note that this may introduce other issues such as potential instabilities in crafting or frequent task switching which are incredibly costly given the high energy startup cost of a fusion craft.

# Using Systems to model power consumption and modify production accordingly

A perplexing problem occurs. The input to our system is a stepped input, it is either on or off with the ability to scale by a very specific amount. 

In addition, only switching our input on adds a loss function of some extra lost EU (as a large packet). This means that we have a system which obeys hysterysis. Analysis of these kinds of systems is difficult and requires careful linearization of the system to produce energy correctly

The ultimate hope is that a PID or equivalent MIMO controller can be implemented to analyze the energy by swapping linear models as needed to perform the correct output. 

It might also just be possible to predict future states using a "time til dead" metric on the power grid by monitoring current consumption 

TODO: 
- Work on transfer function for this problem
- Create basic system layout for feedback (Energy desired, Actual Energy) OR design Python sim to test functionality in time domain

# Priority System

Tasks with priorities are given to each fusion reactor (which is treated like a processor core) based on the tasks already scheduled. Below is a table of the scheduler priority of tasks. These are self explanatory.

| Task             | Priority |
| ---------------- | -------- |
| Power Generation | 3        |
| Crafting (AE2)   | 2        |
| Manual Craft     | 1        |
| Idle             | 0        |

### Project Goals

To have fun designing and building a complex system in Minecraft to automatically model a difficult to manage power system.

To analyze a complex non-linear system using engineering control theory if possible.
