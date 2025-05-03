# 5100_Final_Project
This project implements a simulation of a dice game using Monte Carlo methods. It features three main classes: Die, Game, and Analyzer. The Die class simulates a die with multiple faces and variable weights, the Game class simulates rolling multiple dice, and the Analyzer class analyzes the results of the game.

# Synopsis

Die class
The Die class represents a die with a specified set of faces. You can modify the weights of the faces and roll the die multiple times.

'''
import numpy as np
from montecarlo import Die
faces = np.array([1, 2, 3, 4, 5, 6])
die = Die(faces)
rolls = die.roll(5)
print(rolls)
'''

Game class
The Game class simulates a game involving multiple dice. It supports rolling all dice a specified number of times and displaying the results in either wide or narrow format.

'''
from montecarlo import Game, Die
die1 = Die(np.array([1, 2, 3, 4, 5, 6]))
die2 = Die(np.array([1, 2, 3, 4, 5, 6]))
game = Game([die1, die2])
game.play(5)
print(game.show(form='wide'))
'''
