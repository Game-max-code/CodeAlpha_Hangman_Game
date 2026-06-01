import random
def play_hangman():
    word_list = ["python", "intern", "coding", "script", "hacker"]
    chosen_word = random.choice(word_list)
    guessed_letters = []
    incorrect_guesses = 0
    max_attempts = 6  
    print("Welcome to Hangman!")
    print(f"You have {max_attempts} incorrect guesses allowed.")
# Main code:
    while incorrect_guesses < max_attempts:
        display_word = ""
        for letter in chosen_word:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "  
        print(f"\nWord to guess: {display_word}")
        if "_" not in display_word:
            print("\nCongratulations! You guessed the word correctly!")
            break
        guess = input("Guess a letter: ").lower()
        if guess in guessed_letters:
            print("You already guessed that letter. Try again.")
            continue
        guessed_letters.append(guess)
        if guess in chosen_word:
            print(f"Good job! '{guess}' is in the word.")
        else:
            incorrect_guesses += 1
            print(f"Wrong guess. '{guess}' is not in the word.")
            print(f"Incorrect guesses left: {max_attempts - incorrect_guesses}")
    if incorrect_guesses == max_attempts:
        print(f"\nGame Over! You've run out of guesses. The word was '{chosen_word}'.")

# Run the game
if __name__ == "__main__":
    play_hangman()
