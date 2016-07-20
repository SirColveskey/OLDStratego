# Stratego
Java (cop3252) Final Project - Implementing Stratego as a GUI Java Application

This project will have included files:
- Board.png
- Blue[1-9].png
- BlueB.png
- BlueF.png
- Red[1-9].png
- RedB.png
- RedF.png
- - BLUE.png
- RED.png
****I forgot the spy, will have to add it***

Classes: 
Piece
  Attributes:
    Board board
    BoardSquare square
    string Color
    char/int Rank
    int Range -- Normally 1, 10 for rank == 9, 0 for rank == Flag and rank == Bomb
    pair/tuple Position
    boolean Alive
    boolean Attacks -- True for everything but rank == Flag and rank == Bomb
    image Piece
    image Insignia
  Functions:
    int Attack(Piece) -- returns -1 for dies, 1 for kills, 0 for draw
    boolean Move(Position) -- checks to see if it can move to position, if so moves there, attacks if neccesary
    void Die() -- informs board of death, tells square to kill it
BoardSquare
  Attributes:
    Piece Occupant = Null -- Defaults to Null ***We may have to make a blank piece instead of using Null
    pair/tuple Position
    boolean Water = False -- Only water spaces <So a square is moveable through only if Occupant == Null and Water == False>
  Functions:
    void MakePiece(int Rank, string Color) -- Occupant = Piece(Color,Rank)
    void ClearPiece() -- Occupant = Null
Board
  Attributes:
    BoardSquare[10][10] Squares
    string Mode -- Conditions include "Start" "Placement1" "Placement2" "Playing" "Victory"
    string Turn -- Red or Blue
    int[10] RedPieces -- 0 == bomb, 1-9, Stores the number of each piece still in the game
    int[10] BluePeces
    jlabel[20] Pools -- For the pieces arrays to print in the "Combatant" Boxes
  Functions:
    void SetupMatch() --
    ***void LoadMatch() --
    ***void SaveMatch() --
    void Flip() -- Turns off all pieces that are showing, turns on all pieces that aren't
    void CheckGameover() -- Makes sure there is a viable move to be made (in Stratego it's gameover if you can't move)
    void GetMove() -- Gets the players move and checks it for compliance 
    void UpdatePools()
    void AcceptDeath(int rank) -- Called when a piece dies, decrements its rank
    void Muster() -- Calls all pieces and tallies their ranks, resetting RedPieces and BluePieces
    void FlagCapture(string Color) -- Color has captured the other teams flag and wins.
Driver
  Attributes:
    Board board
    GameMouse mouse
  Functions:
    void Menu()
    void GameLoop()
GameMouse
  Attributes:
    Mouse mouse
    Piece pieceOnMouse
  Functions:
    void SetPiece()
    void MakeSelection()
    void ClearSelection()
