# Egg-Breaking-Brain-Teaser

This program was written to empirically prove the solution of a brain teaser. The original brain teaser goes like this:

Imagine a skyscraper 100 stories tall.  You are given two identical eggs that will break when they are dropped from a certain story or any stories above it. You can drop the eggs as many times as you want (until they break), and the eggs are magical, so as long as they don't break, they don't get any weaker from consecutive drops.  What is the best method for dropping the eggs to find the highest story at which they can safely be dropped?  Your method will be judged by the number of required drops in the worst case scenario. Your method is considered invalid if under any circumstances it is incapable of finding the highest safe floor.

For example, if your method is to attempt a binary search, the worst case would go as follows:
  1) You drop the egg at floor 50.  It breaks. You have 1 Egg left
  2) Starting from floor 1, you drop the egg from every consecutive floor
  3) You finally drop the egg from floor 49, and it doesn't break. 
  4) Total number of drops: 50
  
#The Solution
Full calculations for most of the equations referenced below can be found as handwritten, mostly legible notes in the accompanying file named "Proof"
Drop the first egg at a certain interval, for example every 5th floor, until it breaks. Once it breaks, go down to one floor above the last floor that you safely tested from, and then start testing consecutive floors

Example
  1)You drop the egg at floor 5. It doesn't break
  2)You drop the egg at floor 10. It doesn't break
  3)You drop the egg at floor 15. It breaks.
  4)You drop the egg at floor 11. It doesn't break
  5)You drop the egg at floor 12. It breaks. Success
  
If y = the number of drops required in the first case
And a = the interval size

y = 100/a + a -1
To find the optimal solution, take the derivative of y with respect to a, set it equal to 0, and solve for a, which turns out to be 10.

If we replace 100 with n, to represent the number of floors, the solution becomes
a = n^(1/2)

If we use 3 eggs instead of 2 where
a= the interval the first egg is dropped at
b= the interval the second egg is dropped at (Once the first egg breaks, go the the last safe floor, and drop at every b floors)
y = n/a + a/b + b + 1
After  taking 2 partial derivatives and setting them both equal to 0, we find that
a = n ^ (2/3)
b = n ^ (1/3)

If we extrapolate this pattern and say that
n = the number of stories
j = the number of eggs

x_1 = the interval for the first egg
x_2 = the intervale for the second egg
x_3 = the interval for the third egg
.
.
x_(j-1) = the interval for the second to last egg (because the last egg is dropped consecutively

We find that
x_i = n ^ ((j-i)/j)

