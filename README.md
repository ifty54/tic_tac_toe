# tic_tac_toe
board = [[" " for i in range(3)] for j in range(3)]

def draw_board():
  print("  0 1 2")
  for i in range(3):
    print(f"{i} {board[i][0]}|{board[i][1]}|{board[i][2]}")
    if i != 2:
      print("  -----")

def get_move(player):
  while True:
    row = input(f"{player}, enter row: ")
    col = input(f"{player}, enter col: ")
    try:
      row = int(row)
      col = int(col)
      if row in [0, 1, 2] and col in [0, 1, 2]:
        if board[row][col] == " ":
          board[row][col] = player
          return
        else:
          print("That space is already occupied!")
      else:
        print("Invalid move!")
    except:
      print("Invalid input!")

def check_win(player):
  # check rows
  for row in board:
    if row == [player, player, player]:
      return True
  # check cols
  for col in range(3):
    if board[0][col] == player and board[1][col] == player and board[2][col] == player:
      return True
  # check diagonals
  if board[0][0] == player and board[1][1] == player and board[2][2] == player:
    return True
  if board[0][2] == player and board[1][1] == player and board[2][0] == player:
    return True
  return False

def main():
  while True:
    draw_board()
    get_move("X")
    if check_win("X"):
      print("X wins!")
      break
    draw_board()
    get_move("O")
    if check_win("O"):
      print("O wins!")
      break

main()
