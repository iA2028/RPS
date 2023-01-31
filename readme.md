Rock-Paper-Scissors

This is a Vue.js based Rock-Paper-Scissors game. The user can select the number of matches to play and can choose rock, paper, or scissors to play against the computer. The game keeps track of the number of wins and losses, and displays the results of each match. A gif is displayed based on the outcome of each match.

Features

Select the number of matches to play (minimum of 3, maximum of 5)
Play rock, paper, or scissors against the computer
Display the result of each match
Keep track of wins and losses
Display a gif based on the outcome of each match
Components

The main game component is Rock-Paper-Scissors
The end game component is EndPage
Data

The game component has data properties for the player's choice, the computer's choice, the result of each match, the number of wins, the number of losses, and the gif to be displayed.

Methods

The game component has several methods:

play() to play a round of the game
resetGame() to reset the game
endGame() to end the game
getComputerChoice() to determine the computer's choice
getResult() to determine the result of each match
Styling

The styles for the game are scoped to the component and use CSS to style the background, buttons, and text.

This project took maybe 3 hours and the second one took an extra hour to rig the server so that it would be playable 

I created a second version the same day with a server componet that allows for multiplayer functionality

