# Statistics-ML-Prblm-solving
Here i am adding hands-on practice.


1.Create the  program simulates a set of coin tosses and calculates the probability of heads and tails based on the number of tosses. It also calculates the theoretical probability of rolling a specific number on a standard six-sided die.

Input format :
The program takes two inputs:

Number of coin tosses — an integer N (must be ≥ 0)

Desired dice number — an integer D (must be between 1 and 6)

Output format :
Coin Toss Results:

Total number of heads and tails observed

Probability of heads (rounded to two decimal places)

Probability of tails (rounded to two decimal places)

Dice Roll Probability:

The theoretical probability of rolling the desired number on a 6-sided die (as a fraction and decimal)

If inputs are invalid, appropriate error messages are shown.

Code constraints :
num_tosses must be a non-negative integer

Example: 0, 10, 100 are valid.
desired_dice_number must be an integer between 1 and 6

Only values from 1 to 6 are allowed.
If num_tosses is 0, the program should show a message and not calculate probabilities.

Inputs must be valid integers

If not, the program should display an error and stop.
Coin tosses should be randomly chosen as either 'Head' or 'Tail' for each toss.

Dice probability is fixed
The chance of rolling any number from 1 to 6 is always 1/6.

Probabilities should be rounded:

Coin toss results: rounded to 2 decimal places
Dice roll probability: shown as both fraction and 4-digit decimal (e.g., 0.1667)

Input 1 :
10
3


Output 1 :
Enter number of coin tosses: Enter desired dice number (1–6): 
--- Coin Toss Results ---
Head: 4, Tail: 6
Probability of Head: 0.40
Probability of Tail: 0.60

--- Dice Roll Probability ---
The probability of rolling a 3 is: 0.1667
Which is also: 1/6

