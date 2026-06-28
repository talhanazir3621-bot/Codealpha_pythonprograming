# Codealpha_pythonprograming
This repository contains my project developed as part of the CodeAlpha Internship. It showcases my implementation, programming skills, and practical understanding of software development concepts. The project includes the complete source code, documentation, and required resources.
# Task 1
import random

words = ["python", "computer", "network", "gaming", "developer"]

word = random.choice(words)

guessed_letters = []
wrong_guesses = 0
max_wrong_guesses = 6

print("Welcome to Hangman!")
print("Guess the word one letter at a time.")

while wrong_guesses < max_wrong_guesses:

    display_word = ""

    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)
    print("Wrong guesses left:", max_wrong_guesses - wrong_guesses)

    if "_" not in display_word:
        print("\nCongratulations! You guessed the word.")
        break

    guess = input("Enter a letter: ").lower()

    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in word:
        print("Correct!")
    else:
        wrong_guesses += 1
        print("Wrong!")

if wrong_guesses == max_wrong_guesses:
    print("\nGame Over!")
    print("The correct word was:", word)

print("Thanks for playing!")


# Task 2
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "MSFT": 420,
    "AMZN": 170
}

portfolio = {}
total_value = 0

print("Stock Portfolio Tracker")
print("\nAvailable Stocks:")

for stock, price in stock_prices.items():
    print(f"{stock} : ${price}")

print("\nType 'done' when you have finished.\n")

while True:

    stock = input("Enter stock symbol: ").upper()

    if stock == "DONE":
        break

    if stock not in stock_prices:
        print("Stock not available.")
        continue

    try:
        quantity = int(input("Enter quantity: "))

        if quantity <= 0:
            print("Quantity must be greater than 0.")
            continue

    except ValueError:
        print("Please enter a valid number.")
        continue

    portfolio[stock] = portfolio.get(stock, 0) + quantity

print("\nPortfolio Summary")
print("-" * 30)

summary = ""

for stock, quantity in portfolio.items():

    value = stock_prices[stock] * quantity
    total_value += value

    print(f"{stock} | Quantity: {quantity} | Value: ${value}")

    summary += f"{stock} | Quantity: {quantity} | Value: ${value}\n"

print("-" * 30)
print(f"Total Investment Value: ${total_value}")

with open("portfolio_summary.txt", "w") as file:
    file.write("Portfolio Summary\n")
    file.write("-" * 30 + "\n")
    file.write(summary)
    file.write("-" * 30 + "\n")
    file.write(f"Total Investment Value: ${total_value}")

print("\nPortfolio saved to portfolio_summary.txt")


