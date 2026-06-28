# Codealpha_pythonprograming
This repository contains my project developed as part of the CodeAlpha Internship. It showcases my implementation, programming skills, and practical understanding of software development concepts. The project includes the complete source code, documentation, and required resources.


import random

# -----------------------------------------
# CodeAlpha Internship
# Task 1: Hangman Game
# -----------------------------------------

# List of predefined words
WORDS = [
    "python",
    "computer",
    "network",
    "gaming",
    "developer"
]

# Select a random word
secret_word = random.choice(WORDS)

# Game variables
guessed_letters = []
incorrect_guesses = 0
max_attempts = 6

print("=" * 50)
print("           HANGMAN GAME")
print("=" * 50)
print("Guess the hidden word one letter at a time.")
print(f"You have {max_attempts} incorrect guesses.\n")

# Main game loop
while incorrect_guesses < max_attempts:

    # Display current progress
    display_word = ""

    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word.strip())
    print(f"Remaining Attempts: {max_attempts - incorrect_guesses}")

    if guessed_letters:
        print("Guessed Letters:", " ".join(sorted(guessed_letters)))
    else:
        print("Guessed Letters: None")

    # Check if the player has guessed the whole word
    if "_" not in display_word:
        print("\nCongratulations! You guessed the word correctly.")
        break

    # Get user input
    guess = input("\nEnter a letter: ").lower().strip()

    # Validate input
    if len(guess) != 1:
        print("Please enter only one letter.")
        continue

    if not guess.isalpha():
        print("Please enter a valid alphabet letter.")
        continue

    if guess in guessed_letters:
        print("You have already guessed that letter.")
        continue

    guessed_letters.append(guess)

    # Check guess
    if guess in secret_word:
        print("Correct!")
    else:
        incorrect_guesses += 1
        print("Incorrect!")

# If player loses
if incorrect_guesses == max_attempts:
    print("\nGame Over!")
    print(f"The correct word was: {secret_word}")

print("\nThank you for playing Hangman!")
