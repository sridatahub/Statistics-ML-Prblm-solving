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


import sys
import random
try:
    n = int(input("Enter number of coin tosses: "))
    d = int(input("Enter desired dice number (1–6): "))
except ValueError:
    print("Invalid input")
    sys.exit()

results = [random.choice(['Tail','Head']) for _ in range(n)]

no_heads = results.count('Head')
no_tails = results.count('Tail')

total = len(results)

prob_head = no_heads/total
prob_tail = no_tails/total

print("\n--- Coin Toss Results ---")


print(f"Head: {no_heads}, Tail: {no_tails}")
print(f"Probability of Head: {prob_head:.2f}")

print(f"Probability of Tail: {prob_tail:.2f}\n")


print("--- Dice Roll Probability ---")

die_prob = 1/6

print(f"The probability of rolling a {d} is: {die_prob:.4f}")
print("Which is also: 1/6")



Program Description

Create the program analyzes customer preferences for two types of coffee—Latte and Black Coffee—across three age groups: 18–25, 26–40, and 40+. It calculates the probability that older customers (age 40 and above) prefer Black Coffee, both jointly and conditionally, and assesses whether age influences this preference.

Input format :
The program asks the user to input the number of customers who prefer each coffee type for each age group. Specifically:

For age group 18–25: number of customers who prefer Latte and Black Coffee

For age group 26–40: number of customers who prefer Latte and Black Coffee

For age group 40+: number of customers who prefer Latte and Black Coffee

All inputs must be non-negative integers.

Output format :
After inputs are provided, the program outputs:

A data summary table showing the counts for each coffee preference by age group.

The joint probability of a customer being 40 or older and preferring Black Coffee.

The conditional probability of preferring Black Coffee given the customer is 40 or older.

The overall probability of preferring Black Coffee across all customers.

A conclusion on whether age (specifically being 40 or older) influences Black Coffee preference, based on whether the conditional probability significantly differs from the overall probability.

Code constraints :
All counts must be integers ≥ 0.

If the total number of customers is zero, the program exits with an error message.

If there are no customers in the 40+ group, the conditional probability cannot be computed, and the program exits with an error message.




2.
