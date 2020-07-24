#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)

The driver of runtime complexity here is the number of iterations of the `while` loop. The loop will run n*n*n (or n^3) times, for an initial runtime complexity of O(n^3). Inside each loop, addition is of O(1) complexity. Multiplication of two m-digit numbers has a minimum complexity of O(n log n), so overall computation complexity will depend on the size of the values used; ignoring multiplication, though, the computational complexity is O(n^3).

b)

Computational complexity here is driven by the nested loops. The `for i` loop will run n times, for an initial complexity of O(n). The nested `while j` loop will run a number of times equal to the lowest integer greater than or equal to the base-2 log of n +1, since j starts at 1 and doubles for each iteration. This will be shorter for smaller n and longer for larger n, but grows with n with O(log n). Ony arithmetic operations are used within the j loop. Since the loops are nested, the computational complexity multiplies, for overall O(n log n).

c)

Complexity here is due to recursive rather than iterative repetition. Each time the function is called with input n, it makes a single recursive function call using the value n-1, and stops (and sends the output back up the recursion pile) when the input == 0. There will be n+1 function calls on the way "down", and n+1 values returned on the way back "up". There are no loops, conditionals, or multiple recursive function calls, and other than calls and replies only arithmetic operations are used. Computational complexity is O(n).

## Exercise II

The question indicates that the goal is to minimize "dropped + broken" eggs. This is not clear as to whether *all* dropped eggs are to be counted, or whether only eggs that are dropped *and* broken are to be minimized.

The solution for finding f in the latter case (minimizing only eggs which are dropped *and broken*) is trivial. Start from the first floor, drop an egg, then proceed to the next floor iff the egg does not break. The first floor where the dropped egg breaks is floor f, and only one egg has been broken. The only condition where f can be confirmed without breaking *any* eggs is if f=n+1 (i.e. the egg will survive a fall from any floor), which will be confirmed when an egg dropped from floor n does not break.

The approach changes if the goal is to minimize the total number of eggs *dropped*. In this case, the goal is to find f with the smallest possible number of drops, which is accomplished by maximizing the information gained with each egg drop, which is the same as maximizing the expectation value of the number of possible values for f eliminated with each drop. The approach is as follows:
1) Choose a floor from which to drop the next egg. This should be the average of the floor numbers of the highest and lowest remaining possibilities (which on the first selection will be the lowest and highest floors). Rounding down in cases where an even number of floors remain improves the end behavior of the algorithm, and slightly improves the expectation value of the number of floors excluded.
2) If the egg breaks, eliminate all higher floors from the range of possible floors, since the lowest height from which the egg will break (f, what is to be found) is at or below the current floor.
3) If the egg does *not* break, eliminate all lower floors *and* the current floor from the range of possible floors, since the lowest height from which the egg will break must be higher.
4) After this elimination, if only one floor remains, that is floor f.
5) If more than one floor remains, go back to step 1 with the new (reduced) range of possible floors. Continue until the algorithm completes at step 4.