# Markdown timer

+ Make a settings hamburger menu so where you add: 
+ The graph

The entire point of the app is to see that you are effeciant and not wasting time between tasks, but at the same time not doing to much. A health balance, so there should be a function that which makes 3 versions of a schedule. 1 fast 2 standard and 3 slow. This just increase the time for each task by some % such that the user can adapt to the tempo. 

The app is already working so just try not to messthings up.

Try to leverage localstorage as much as possible and try to make the app more complete.


1. Remove the heading for more space, (add a small text somewhere, where it says md-timer), keep the "standard tempo" or similar text at the top.

2. Make the textarea into a proper editor. Have an editmode, have a mode where you cannot select text but rearrange the order of the tasks. Add small buttons within the editor for convenience, perhaps some sec/min/hour solution.

3. Always start tasks with captial letter. If the name of the task is very long come up with a way to handle this, maybe if you press the tasks name it show the entire task name at some point. 

4. "Timer Overview" can be removed and should be included in the editor. Total task time should be included as usual but add target time as well.

5. Put the start button at a better place, it is now at the bottom and is hard to find if you are at the top sometimes. 

6. If you click outside of the timers body (the countdown clock that is rendered when running, with the back, pause skip, stop), you should not cancel the timer, but minimize it. Also see if you can combine those 4 buttons into less buttons.

7. Instead of having the graph as a separate function include it in the actual timer, make it so that you can open it in 1 button press while in the timer view.

8. There should only be one big continious session such that you can get the previous runs. Make sure that the graph displays this session in real time.

9. 