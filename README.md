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
