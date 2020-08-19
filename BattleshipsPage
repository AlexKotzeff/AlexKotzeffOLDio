#Alexander Kotzeff
#Basic battleship python game.

boardDimensions = int(input())

board_1 = [["-" for y in range(boardDimensions)]for x in range(boardDimensions)]
board_2 = [["-" for y in range(boardDimensions)]for x in range(boardDimensions)]

#Determine how many turns total and for each player. 

numberOfTurnsPerPlayer = int(input())
numberOfTurnsTotal = numberOfTurnsPerPlayer * 2

#Create function for each board to determine how the boat is formatted.

def createBoat_1(size):
  i = 0
#First check the last digit of the play to determine if the boat is vertical or horizontal 
#If it is 1, i is added to the second digit in the play so that "B"s are added on the X-axis
  if int(coordinates [3]) == 1:
#Make a while loop and stop when i reaches the right number.
    while i < int(coordinates [2]):
#Stop the loop using "break" if the boat goes off the board. 
      if int(int(coordinates [1]) + i) >= boardDimensions:
        break  
#If the boat is not going off the board, 
      board_1[int(coordinates [1]) + i][x] = "B"
      i += 1
#If the last digit is not 1, then it is zero and the boat is placed horizontally. 
  else:
    while i < int(coordinates[2]):
#Break if going off board
      if int(int(coordinates [0]) + i) >= boardDimensions:
        break
#Since the boat is horizontal, i is added on the Y axis
      board_1[y][int(coordinates[0]) + i] = "B"
      i += 1

#Do the same for the second board
def createBoat_2(size):
  i = 0
  if int(coordinates [3]) == 1:
    while i < int(coordinates [2]):
      if int(int(coordinates [1]) + i) >= boardDimensions:
        break
      board_2[int(coordinates [1]) + i][x] = "B"
      i += 1
  else:
    while i < int(coordinates[2]):
      if int(int(coordinates [0]) + i) >= boardDimensions:
        break
      board_2[y][int(coordinates[0]) + i] = "B"
      i += 1
  
#Use the createBoat_X function in this loop to add "B"s and to switch between players

i = 1
#Make a while loop that stops when there are no more boats being added.
while (i <= numberOfTurnsTotal):
  playerMove = input()
#Split up the input into a list so each part can be read indevidually. 
  coordinates = playerMove.split()
#Use modulous to switch between players. 
  if i%2 != 0:
    x, y, size, dir = map(int,coordinates)
    createBoat_1(int(coordinates[2]))
  else:
    x, y, size, dir = map(int,coordinates)
    createBoat_2(int(coordinates[2]))
  i+=1
  
#Print the lists into a table to show boat locations 

ROWS = boardDimensions
COLUMNS = boardDimensions

for i in range(ROWS):
  for j in range(COLUMNS):
    print(board_1[i][j], end="")
  for j in range(COLUMNS):
    if j == 0:
      print("\t", end="")
  for j in range(COLUMNS):
    print(board_2[i][j], end="")
  print()

#Separate the two boards

print()

#Add the shots to the list 
#Determine number of shots total and for each player
numberOfShotsPerPlayer = int(input())
numberOfShotsTotal = numberOfShotsPerPlayer * 2

#Make a list that stops when no more shots are being fired
i = 1
while i <= numberOfShotsTotal:
  shotCoordinates = input().split()
#Player one goes first again and alternate players using the modulous function. 
#Make changes to player 2's board based on where player one shot. 
  if i%2 != 0:
#Make sure the shot is on the board
    if int(shotCoordinates[0]) < boardDimensions and int(shotCoordinates[1]) < boardDimensions:
      board_2[int(shotCoordinates[1])][int(shotCoordinates[0])] = "X" 
#Switch to making changes on player 1's board. 
  else:
    if int(shotCoordinates[0]) < boardDimensions and int(shotCoordinates[1]) < boardDimensions:
      board_1[int(shotCoordinates[1])][int(shotCoordinates[0])] = "X"
  i += 1

#Print the table again but with shots added

for i in range(ROWS):
  for j in range(COLUMNS):
    print(board_1[i][j], end="")
  for j in range(COLUMNS):
    if j == 0:
      print("\t", end="")
  for j in range(COLUMNS):
    print(board_2[i][j], end="")
  print()

print()

#Determine if the players still have boats
#Assume there are no more boats on the board
player1HasBoats = False 
player2HasBoats = False

#Read each element on the board and change the status to True if a "B" is found
for i in range(boardDimensions):
  for j in range(boardDimensions):
    if board_1[i][j] == "B":
      player1HasBoats = True
    if board_2[i][j] == "B":
      player2HasBoats = True

#If they both have boats it is a draw
if player1HasBoats == True and player2HasBoats == True:
  print("Draw")

#If only one player has boats left they win
elif player1HasBoats == True and player2HasBoats == False:
  print("P1 Win")

elif player1HasBoats == False and player2HasBoats == True:
  print("P2 Win")

#If neither players have boats left then all are destroyed
else:
  print("All destroyed")
