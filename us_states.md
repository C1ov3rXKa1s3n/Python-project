# US STATES FINDING PROJECT
In this project we will create the project of finding the us states on us map.
We have done python implementation of the game.
[Play the game](https://www.sporcle.com/games/Matt/find_the_states)

```python
from turtle import Screen, Turtle
import pandas as pd
pdfile = pd.read_csv("50_states.csv")
screen = Screen()
screen.title("U.S. States Games")
screen.addshape("ustates.gif")
tur = Turtle()
is_on = True
tur.shape("ustates.gif")
states_done = 0
states_list = []
while is_on:
	answer = screen.textinput(f"Guess the state Correct : {states_done}/50", "What is the state name")
	answer = answer.capitalize()
	turtle = Turtle()
	turtle.ht()
	for index, state in pdfile.state.items():
		if answer == state:
			turtle.penup()
			turtle.goto(pdfile.x[index],pdfile.y[index])
			turtle.write(pdfile.state[index])
			states_done += 1
			states_list.append(pdfile.state[index])
		elif answer.lower() == "quit" or answer.lower() == "exit":
			is_on = False
		elif states_done == 50:
			is_on = False
for state in pdfile.state:
	if state not in states_list:
		with open("learn_state.txt", "a") as files:
			files.write(f"{state} \n")
```
# EXPLANATION
