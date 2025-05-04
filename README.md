# 5100_Final_Project
This project implements a simulation of a dice game using Monte Carlo methods. It features three main classes: Die, Game, and Analyzer. The Die class simulates a die with multiple faces and variable weights, the Game class simulates rolling multiple dice, and the Analyzer class analyzes the results of the game.

# Synopsis

#Die class
The class features a die that has N faces with each face containing a unique symbol that can be alphabetic or numeric.
In addition, each face has a default equal weight of 1.0. However, the weights can be altered after the object is created.
The die can be rolled one or more times, which returns random outcomes based on weights.

'''
import numpy as np
from montecarlo import Die
faces = np.array([1, 2, 3, 4, 5, 6])
die = Die(faces)
rolls = die.roll(5)
print(rolls)
'''

#Game class
A Game consists of rolling one or more similar Die objects one or more times.
Each die in the game must have the same number of sides and associated faces, however their weights may differ.
This class supports playing the game (i.e., rolling all dice) and retrieving the results of the most recent play in wide or narrow format.

'''
from montecarlo import Game, Die
die1 = Die(np.array([1, 2, 3, 4, 5, 6]))
die2 = Die(np.array([1, 2, 3, 4, 5, 6]))
game = Game([die1, die2])
game.play(5)
print(game.show(form='wide'))
'''

#Game class
 This class takes a Game object and looks at the results of its most recent play.  
    It includes methods to:
    - Count how many rolls had all matching faces (a jackpot)
    - Show how often each face appeared in every roll
    - Count unique combinations of faces (ignoring the order of dice)
    - Count unique ordered rolls (keeping the order of dice)

'''
from montecarlo import Analyzer, Game, Die
import numpy as np

die1 = Die(np.array([1, 2, 3, 4, 5, 6]))
die2 = Die(np.array([1, 2, 3, 4, 5, 6]))
game = Game([die1, die2])
game.play(5)

analyzer = Analyzer(game)

print("Jackpot count:", analyzer.jackpot())
print(analyzer.face_counts_per_roll())

# API

#Die class

def __init__(self, faces)
Initializes the die with the provided faces. 
The input must be a NumPy array or it will result in a TypeError.
All the faces must be different, otherwise it will raise a ValueError. 
The faces and their weights are stored in a table where the face values act as labels.

def change_weight(self, face, new_weight)
Changes the weight of a specific face on the die.

def roll(self, times=1)
Rolls the die a specified number of times and returns the outcomes.

def show(self)
Returns a copy of the die’s internal data table.

#Game class

def __init__(self, dice_list)
Initializes the Game with a list of Die objects.
The parameter is dice_list and represents a list of die objects.
A TypeError will be raised if any item in the list does not appear to be a die

def play(self, rolls) 
Rolls all dice a specified number of times, storing the result in wide format.
The parameter is num_rolls, which tells how many times to roll each die.
The results are stored in a table where each column is a die, and each row is a roll.

def show(self, form='wide')
Returns the results of the most recent play.

The parameter is form, which can be 'wide' (default) or 'narrow'.
- 'wide' shows one column for each die and one row for each roll.
- 'narrow' shows each result in its own row with extra labels.
Raises a ValueError if the form is not valid or if the game hasn’t been played yet.

#Analyzer class

def __init__(self, game)
Initializes the Analyzer with a Game object.
The parameter is game, which should be a Game that has already been played.
If something other than a Game is passed in, it will raise a ValueError.

def jackpot(self)
Counts the number of rolls where all dice have the same face (jackpot).
Returns the number of jackpot rolls as an integer.

def face_counts_per_roll(self)
Computes the count of each face per roll.
Returns a table where each row is a roll, each column is a face, and each cell shows how often that face came up in that roll.

def combo_count(self)
Counts how often each unique set of faces appeared in the rolls, ignoring the order of the dice.
Returns a table showing each combination and how many times it happened.

def permutation_count(self)
Counts how often each exact order of faces appeared in the rolls, keeping the dice order in mind.
Returns a table showing each unique ordered roll and how many times it happened.

























