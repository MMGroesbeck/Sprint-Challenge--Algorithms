#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)

The driver of runtime complexity here is the number of iterations of the `while` loop. The loop will run n*n*n (or n^3) times, for an initial runtime complexity of O(n^3). Inside each loop, addition is of O(1) complexity. Multiplication of two m-digit numbers has a minimum complexity of O(n log n), so overall computation complexity will depend on the size of the values used; ignoring multiplication, though, the computational complexity is O(n^3).

b)

Computational complexity here is driven by the nested loops. The `for i` loop will run n times, for an initial complexity of O(n). The nested `while j` loop will run a number of times equal to the lowest integer greater than or equal to the base-2 log of n +1, since j starts at 1 and doubles for each iteration. This will be shorter for smaller n and longer for larger n, but grows with n with O(log n). Ony arithmetic operations are used within the j loop. Since the loops are nested, the computational complexity multiplies, for overall O(n log n).

c)

Complexity here is due to recursive rather than iterative repetition. Each time the function is called with input n, it makes a single recursive function call using the value n-1, and stops (and sends the output back up the recursion pile) when the input == 0. There will be n+1 function calls on the way "down", and n+1 values returned on the way back "up". There are no loops, conditionals, or multiple recursive function calls, and other than calls and replies only arithmetic operations are used. Computational complexity is O(n).

## Exercise II


