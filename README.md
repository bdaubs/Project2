# Project2

|Thread<br>Count|Wall Clock<br>Time|User Time|System Time|Speedup|
|:--:|--:|--:|--:|:--:|
|1|14.59|13.80| 0.58|1.00|
|2| 7.66|13.92| 0.70| 1.90|
|3| 6.17|16.91| 0.65| 2.36|
|4| 4.83|16.70| 0.92| 3.02|
|5| 4.17|16.82| 0.93| 3.50|
|6| 3.60|16.83| 1.17| 4.05|
|7| 3.06|16.73| 1.14| 4.77|
|8| 2.82|16.77| 1.32| 5.17|
|16| 2.05|18.07| 3.14| 7.12|
|24| 1.99|18.59| 6.25| 7.33|
|32| 1.92|18.02|13.92| 7.60|
|40| 1.97|17.72|18.57| 7.41|
|48| 1.89|17.06|25.22| 7.72|
|56| 1.97|16.85|24.42| 7.41|
|64| 2.35|16.79|29.54| 6.21|
|72| 2.45|17.24|13.85| 5.96|
|80| 1.94|17.38|21.80| 7.52|

![image](https://github.com/user-attachments/assets/c4ffeea2-a408-4661-9e54-7575059d50ab)

Question: Notice that there is a maximum speed-up factor, but not necessarily using the most threads. Make a guess (i.e., write a short paragraph) as to why you think more threads aren’t necessary better. Here’s a hint: think about a group of people waiting to go through a turnstile (like at BART or Disney World). Are more people able to go through it just because there are more people?
The maximum speedup factor seems to occur at around 32 threads. Maybe this has something to do with how memory runs in the processor. 
If only 32 threads can be processed at a time, having more than 32 threads wouldn't really speed anything up. There would be a bottleneck at 32.

Question: Do you think it’s possible to get “perfect scaling” — meaning that the (1-p) terms is zero?
Yes, if all the code in the program is parallel, thus p = 1 and (1-1) is 0.

main program 0.007809873 s
results output 4.67e-07 s
main program 2.531417181 s

(0.007809873 s + 4.67e-07 s) / 2.531417181 s = 0.0030853626 s
This is our s, so
1 - 0.0030853626 = 0.9969146374 p
Question: For your own timings, compute your expected speed-up for 16 cores.
speed-up = 1 / (1 - 0.9969146374 + (0.9969146374 / 16 )) = 15.29


$$ speedup = \frac{1}{1 - 0.9969146374 + \frac{0.9969146374}{16}} = 15.29$$

One final Question: in reviewing the graph of speed-ups to number of threads, note that we get pretty linear (when you plot the dots, they’re pretty close to being a line) speed-up. What’s the slope of that line? (Pick two values, like for one and seven threads, and do the rise-over-run thing you learned in Algebra). Does that linear trend continue as we add more threads? What do you think causes the curve to “flatten out” when we use large thread counts?

From 2 to 3 threads, the slope of speed-up is about 0.66. It decreases and eventually flattens out at about 32 threads. As we had mentioned before this is probably because the CPU only has 32 cores and so more threads won't speed up the process any further.
