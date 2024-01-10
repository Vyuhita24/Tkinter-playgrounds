import tkinter as tk
from tkinter import Tk, Toplevel,Frame, Label, Button, Entry, messagebox, TOP,StringVar

import random

#code for the main window.

root = Tk()
root.title("TKinter Playgrounds")
root.iconbitmap('star_Vyx_icon.ico')
root.geometry("370x640")
root.configure(bg="purple")
my_font = ("Arial", 14)
button_frame = Frame(root,bg="purple")
response_label = None  # Declare response_label as a global variable
result_label = None  # Declare result_label as a global variable

#code begins for the first game "GUESS THE NUMBER"

def guess_instruct():
    guess_window = Toplevel(root)
    guess_window.title("Make a Guess or Let the Computer Guess")
    guess_window.geometry("370x640")
    guess_window.iconbitmap('star_Vyx_icon.ico')
    guess_window.configure(bg="purple")

    guess_label = Label(
        guess_window,
        text="->There are two buttons\n1. Make a Guess:\n*Have fun by guessing\n the computer's SECRET NUMBER\n2. Let The Computer Guess\n*Have fun by making the computer \nguess YOUR secret number ",
        font=my_font,
        bg="gold"
    )
    guess_label.pack(pady=50)

    make_a_guess = Button(guess_window, text="Make a Guess", font=my_font, bg="gold", command=you_guess)
    make_a_guess.pack(pady=20)

    let_me_guess = Button(guess_window, text="Let The Computer Guess", font=my_font, bg="gold", command=sys_guess)
    let_me_guess.pack()
#Code for "Make A Guess" which is a sub game
def you_guess():
    you_guess_window = Toplevel(root)
    you_guess_window.title("Make a Guess")
    you_guess_window.geometry("370x640")
    you_guess_window.iconbitmap('star_Vyx_icon.ico')
    you_guess_window.config(bg="purple")

    secret_number = random.randint(1, 10)
    guesses = 0

    def check_guess():
        nonlocal guesses
        try:
            guess = int(entry.get())
            guesses += 1

            if guess == secret_number:
                result_label.config(text=f"Congratulations! You guessed it in {guesses} guesses!")
            elif guess < secret_number:
                result_label.config(text="Too low! Try again.")
            else:
                result_label.config(text="Too high! Try again.")
        except ValueError:
            result_label.config(text="Invalid input. Please enter a number.")

    tk.Label(you_guess_window, text="Guess a number between 1 and 10:", font=my_font, bg="gold").pack(pady=10)
    entry = Entry(you_guess_window, font=my_font, width=5, bg="gold")
    entry.pack(pady=10)
    
    submit_button = Button(you_guess_window, text="Submit", font=my_font, bg="gold", command=check_guess)
    submit_button.pack(pady=10)
    
    global result_label  # Declare result_label as a global variable
    result_label = Label(you_guess_window, text="", font=my_font, bg="gold")
    result_label.pack(pady=10)
#The code for "let the computer guess" which is another sub game
def sys_guess():
    sys_guess_frame = Toplevel(root)
    sys_guess_frame.title("Let The Computer Guess")
    sys_guess_frame.geometry("370x640")
    sys_guess_frame.iconbitmap('star_Vyx_icon.ico')
    sys_guess_frame.configure(bg="purple")

    low = 1
    high = 10
    guesses = 0

    response_label = Label(sys_guess_frame, text="", font=my_font, bg="gold")
    response_label.pack(pady=10)

    def computer_guess():
        nonlocal guesses, low, high
        guess = random.randint(low, high)
        response_label.config(text=f"Is {guess} your number?")

        def handle_response(response):
            nonlocal guesses, low, high
            if response == "Yes":
                result_label.config(text=f"YAY! The computer guessed your number in {guesses} guesses!")
            elif response == "No, smaller":
                guesses += 1
                high = guess - 1
                computer_guess()
            elif response == "No, bigger":
                guesses += 1
                low = guess + 1
                computer_guess()

        response_frame = Toplevel(sys_guess_frame)
        response_frame.title("Response")
        response_frame.geometry("320x200")
        response_frame.config(bg="purple")

        result_label = Label(response_frame, text="", font=my_font,bg="gold")
        result_label.pack(pady=10)

        yes_button = Button(response_frame, text="Yes", font=my_font,bg="gold",command=lambda: handle_response("Yes"))
        yes_button.pack(pady=5)

        smaller_button = Button(response_frame, text="No, smaller", font=my_font,bg="gold", command=lambda: handle_response("No, smaller"))
        smaller_button.pack(pady=5)

        bigger_button = Button(response_frame, text="No, bigger", font=my_font,bg="gold", command=lambda: handle_response("No, bigger"))
        bigger_button.pack(pady=5)

    tk.Label(sys_guess_frame, text="Think of a number between 1 and 10.", font=my_font, bg="gold").pack(pady=10)
    tk.Button(sys_guess_frame, text="Press when ready", font=my_font, bg="gold", command=computer_guess).pack(pady=10)

#The code for Rock paper Scissors game

def rps_instruct():
    rps_window = Toplevel(root)
    rps_window.title("INSTRUCTIONS: ")
    rps_window.geometry("370x640")
    rps_window.iconbitmap('star_Vyx_icon.ico')
    rps_window.configure(bg="purple")
    rps_label = Label(rps_window, text="Let us play Rock Paper Scissors\nClick on your choice", bg="gold",font=my_font)
    rps_label.pack(padx=50)
    options = ["rock", "paper", "scissors"]
    user_choice_var = StringVar()
    sys_choice = random.choice(options)

    def give_rock():
        user_choice_var.set("rock")

    rock = Button(rps_window, text="Rock", font=my_font,bg="gold", command=give_rock)
    rock.pack(pady=10)

    def give_paper():
        user_choice_var.set("paper")

    paper = Button(rps_window, text="Paper", font=my_font,bg="gold", command=give_paper)
    paper.pack(pady=10)

    def give_scissors():
        user_choice_var.set("scissors")

    scissors = Button(rps_window, text="Scissors", font=my_font,bg="gold", command=give_scissors)
    scissors.pack(pady=10)

    def determine_winner():
        user_choice = user_choice_var.get()
        result_label.config(text="")
        if user_choice == sys_choice:
            result_label.config(text=f"computer choosed {sys_choice}\nIt's a tie!")
        elif (user_choice == 'rock' and sys_choice == 'scissors') or \
                (user_choice == 'paper' and sys_choice == 'rock') or \
                (user_choice == 'scissors' and sys_choice == 'paper'):
            result_label.config(text=f" computer choosed {sys_choice}\nYou win!")
        else:
            result_label.config(text=f" computer choosed {sys_choice}\nComputer wins!")

    play_button = Button(rps_window, text="Play", font=my_font,bg="gold", command=determine_winner)
    play_button.pack(pady=10)

    result_label = Label(rps_window, text="",bg="gold", font=my_font)
    result_label.pack(pady=10)

#The code for Hangman game

def hangman(root):
    def choose_word():
        words = ["python", "hangman", "programming", "computer", "keyboard"]
        return random.choice(words)

    def display_word():
        return ''.join([letter if letter in guessed_letters else ' _ ' for letter in word_to_guess])

    def make_guess():
        guess = entry_var.get().lower()

        if guess.isalpha() and len(guess) == 1:
            if guess in guessed_letters:
                feedback_var.set("You already guessed that letter. Try again.")
            elif guess in word_to_guess:
                feedback_var.set("Good guess!")
            else:
                feedback_var.set("Incorrect guess.")
                attempts_var.set(attempts_var.get() + 1)

            guessed_letters.append(guess)
            word_display.set(display_word())

            if display_word() == word_to_guess:
                feedback_var.set("Congratulations! You guessed the word.")
                reset_game()
            elif attempts_var.get() == max_attempts:
                feedback_var.set(f"Sorry, you ran out of attempts. The correct word was: {word_to_guess}")
                reset_game()
        else:
            feedback_var.set("Invalid input. Please enter a single letter.")

    def reset_game():
        nonlocal word_to_guess, guessed_letters
        word_to_guess = choose_word()
        guessed_letters = []
        attempts_var.set(0)
        word_display.set(display_word())
        entry_var.set("")
        feedback_var.set("")

    hangman_window = tk.Toplevel(root)
    hangman_window.title("Hangman Game")
    hangman_window.iconbitmap('star_Vyx_icon.ico')
    hangman_window.geometry("370x640")
    hangman_window.configure(bg="purple")

    word_to_guess = choose_word()
    guessed_letters = []
    max_attempts = 6

    word_display = tk.StringVar()
    word_display.set(display_word())

    feedback_var = tk.StringVar()

    tk.Label(hangman_window, text="Welcome to Hangman!", font=("Helvetica", 16), bg="gold").pack(pady=10)
    tk.Label(hangman_window, textvariable=word_display, font=("Helvetica", 14), bg="gold").pack()
    tk.Label(hangman_window, text="Enter a letter:", bg="gold").pack(pady=5)

    entry_var = tk.StringVar()
    tk.Entry(hangman_window, textvariable=entry_var, width=5, bg="gold").pack(pady=5)

    tk.Label(hangman_window, textvariable=feedback_var, fg="black").pack(pady=10)

    attempts_var = tk.IntVar()
    tk.Button(hangman_window, text="Guess", command=make_guess, bg="gold").pack(pady=10)
#The code Tic Tac Toe game
def tic_tac_toe():
    def check_winner():
        for row in board:
            if row.count(row[0]) == len(row) and row[0] != 0:
                return True

        for col in range(3):
            if board[0][col] == board[1][col] == board[2][col] and board[0][col] != 0:
                return True

        if board[0][0] == board[1][1] == board[2][2] and board[0][0] != 0:
            return True

        if board[0][2] == board[1][1] == board[2][0] and board[0][2] != 0:
            return True

        return False

    def check_tie():
        return all(all(cell != 0 for cell in row) for row in board)

    def restart_game():
        for i in range(3):
            for j in range(3):
                buttons[i][j]["text"] = ""
                buttons[i][j]["state"] = "normal"
                board[i][j] = 0

    def handle_click(row, col):
        nonlocal user_symbol, computer_symbol
        if board[row][col] == 0:
            buttons[row][col]["text"] = user_symbol
            buttons[row][col]["state"] = "disabled"
            board[row][col] = user_symbol

            if check_winner():
                messagebox.showinfo("Tic Tac Toe", "You win!")
                restart_game()
            elif check_tie():
                messagebox.showinfo("Tic Tac Toe", "It's a tie!")
                restart_game()
            else:
                computer_move()

    def computer_move():
        nonlocal computer_symbol
        available_moves = [(i, j) for i in range(3) for j in range(3) if board[i][j] == 0]
        if available_moves:
            row, col = random.choice(available_moves)
            buttons[row][col]["text"] = computer_symbol
            buttons[row][col]["state"] = "disabled"
            board[row][col] = computer_symbol

            if check_winner():
                messagebox.showinfo("Tic Tac Toe", "Computer wins!")
                restart_game()
            elif check_tie():
                messagebox.showinfo("Tic Tac Toe", "It's a tie!")
                restart_game()

    user_symbol = "X"
    computer_symbol = "O"

    tic_tac_toe_window = Toplevel(root)
    tic_tac_toe_window.title("Tic Tac Toe")
    tic_tac_toe_window.geometry("300x300")
    tic_tac_toe_window.iconbitmap('star_Vyx_icon.ico')
    tic_tac_toe_window.configure(bg="purple")

    board = [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
    buttons = [[None, None, None], [None, None, None], [None, None, None]]

    for i in range(3):
        for j in range(3):
            buttons[i][j] = Button(tic_tac_toe_window, text="", font=my_font, bg="gold",
                                   command=lambda row=i, col=j: handle_click(row, col))
            buttons[i][j].grid(row=i, column=j, padx=5, pady=5, ipadx=20, ipady=20)
    user_label = Label(tic_tac_toe_window, text=f"User: {user_symbol}", font=my_font, bg="gold")
    user_label.grid(row=3, column=0, pady=5)

    computer_label = Label(tic_tac_toe_window, text=f"Computer: {computer_symbol}", font=my_font, bg="gold")
    computer_label.grid(row=3, column=1, pady=5)

#The buttons on the home page to which the functions are commanded 

guess_number = Button(button_frame, text="   Guess the number   ", font=my_font, bg="gold", command=guess_instruct)
guess_number.pack(side=TOP,padx=10, pady=10)

rps_button = Button(button_frame, text=" Rock Paper Scissors", font=my_font, bg="gold", command=rps_instruct)
rps_button.pack(side=TOP,padx=10,pady=10)

hangman_button=Button(button_frame,text="            Hangman          ", font=my_font, bg="gold", command=lambda: hangman(root))
hangman_button.pack(side=TOP,padx=10, pady=10)

tic_tac_toe_button=Button(button_frame,text="           Tic Tac Toe     ", font=my_font, bg="gold", command=tic_tac_toe)
tic_tac_toe_button.pack(side=TOP,padx=10,pady=10)


welcome = Label(root, text="WELCOME TO TKINTER PLAYGROUNDS\n-Get back to classics", font=my_font,bg="gold")
welcome.pack(side=TOP, pady=50)

button_frame.pack()
root.mainloop()
#End of the code
