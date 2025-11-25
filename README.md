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

2.Create the program analyzes customer preferences for two types of coffee—Latte and Black Coffee—across three age groups: 18–25, 26–40, and 40+. It calculates the probability that older customers (age 40 and above) prefer Black Coffee, both jointly and conditionally, and assesses whether age influences this preference.

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

Sample test cases :
Input 1 :
30
10
25
25
5
25
Output 1 :

Age group: 18–25
Number of customers who prefer Latte: Number of customers who prefer Black Coffee: 
Age group: 26–40
Number of customers who prefer Latte: Number of customers who prefer Black Coffee: 
Age group: 40+
Number of customers who prefer Latte: Number of customers who prefer Black Coffee: 
Data Summary:
       Latte  Black Coffee
18–25     30            10
26–40     25            25
40+        5            25

Joint Probability P(Age 40+ and Black Coffee): 0.2083
Conditional Probability P(Black Coffee | Age 40+): 0.8333

Overall Probability P(Black Coffee): 0.5000
Conditional Probability P(Black Coffee | Age 40+): 0.8333
Age (being 40 or older) influences preference for Black Coffee



import os
import sys
import pandas as pd
def get_int_input(prompt):
    try:
        value = int(input(prompt))
        if value < 0:
            print("Please enter a non-negative integer.")
            sys.exit(1)
        return value
    except ValueError:
        print("Invalid input! Please enter an integer.")
        sys.exit(1)
age_groups = ['18–25', '26–40', '40+']
coffee_types = ['Latte', 'Black Coffee']
data = {coffee: [] for coffee in coffee_types}
for age in age_groups:
    print(f"\nAge group: {age}")
    for coffee in coffee_types:
        count = get_int_input(f"Number of customers who prefer {coffee}: ")
        data[coffee].append(count)
df = pd.DataFrame(data, index=age_groups)
total_customers = df.values.sum()
if total_customers == 0:
    print("No data provided (total customers = 0). Exiting.")
    sys.exit(1)
print("\nData Summary:")
print(df)
joint_prob_older_black = df.loc['40+', 'Black Coffee'] / total_customers
print(f"\nJoint Probability P(Age 40+ and Black Coffee): {joint_prob_older_black:.4f}")
total_40plus = df.loc['40+'].sum()
if total_40plus == 0:
    print("No customers in the 40+ age group, conditional probability undefined.")
    sys.exit(1)

black_40plus = df.loc['40+', 'Black Coffee']
cond_prob_black_given_40plus = black_40plus / total_40plus
print(f"Conditional Probability P(Black Coffee | Age 40+): {cond_prob_black_given_40plus:.4f}")

overall_prob_black = df['Black Coffee'].sum() / total_customers
print(f"\nOverall Probability P(Black Coffee): {overall_prob_black:.4f}")
print(f"Conditional Probability P(Black Coffee | Age 40+): {cond_prob_black_given_40plus:.4f}")

if abs(cond_prob_black_given_40plus - overall_prob_black) < 1e-4:
    print("Age (being 40 or older) does NOT influence preference for Black Coffee.")
else:
    print("Age (being 40 or older) influences preference for Black Coffee.")




3.Create the Python program calculates the total number of possible PIN codes that can be generated using a set of user-defined digits, with two conditions:

Without Replacement: Digits in the PIN do not repeat

With Replacement: Digits can repeat in the PIN

It utilizes Python's itertools module and takes all input directly from the user.

Input format :
The program accepts two user inputs:

Digits: A list of characters or numbers, separated by commas

Example: 0,1,2,3,4

PIN Length: An integer specifying how many digits the PIN should contain

Example: 3

Output format :
After receiving inputs, the program displays:

The total number of unique-digit PINs (no digit is repeated – permutation without replacement)

The total number of PINs with repeated digits allowed (permutation with replacement)

Code constraints :
The list of digits must not be empty

The PIN length must be a positive integer

The PIN length must not exceed the number of digits when calculating permutations without replacement

If any input is invalid, the program will show an error and exit



Sample test cases :
Input 1 :
0,1,2,3,4
3
Output 1 :
PIN Permutation Generator
Enter digits to use for PIN separated by commas (e.g., 0,1,2,3,4): Enter the length of the PIN (e.g., 3): 
PIN Permutations
Total PINs without replacement (unique digits): 60
Total PINs with replacement (digits can repeat): 125



# --- Permutations: PIN Generator ---
import os
import sys
import itertools

# Helper to get a list of digits from user
def get_list_input(prompt):
    raw = input(prompt).strip()
    if not raw:
        print("Input cannot be empty.")
        sys.exit(1)
    return [item.strip() for item in raw.split(',') if item.strip()]

# Helper to get integer input
def get_int_input(prompt):
    try:
        val = int(input(prompt))
        if val <= 0:
            print("Please enter a positive integer.")
            sys.exit(1)
        return val
    except ValueError:
        print("Invalid input! Please enter a valid integer.")
        sys.exit(1)

# User input for digits and PIN length
print("PIN Permutation Generator")
digits = get_list_input("Enter digits to use for PIN separated by commas (e.g., 0,1,2,3,4): ")
pin_length = get_int_input("Enter the length of the PIN (e.g., 3): ")

if pin_length > len(digits):
    print("PIN length exceeds number of available digits (for permutations without replacement).")
    sys.exit(1)

# Generate permutations
permutations_without_replacement = list(itertools.permutations(digits, pin_length))
permutations_with_replacement = list(itertools.product(digits, repeat=pin_length))

# Display results
print(f"\nPIN Permutations")
print(f"Total PINs without replacement (unique digits): {len(permutations_without_replacement)}")
print(f"Total PINs with replacement (digits can repeat): {len(permutations_with_replacement)}")

