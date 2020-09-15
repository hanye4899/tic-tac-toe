# tic-tac-toe
# Code
    X_Win = False
    O_Win = False
    entered_list = [" ", " ", " ", " ", " ", " ", " ", " ", " "]
    matrix = [[entered_list[0],entered_list[1],entered_list[2]],[entered_list[3],entered_list[4],entered_list[5]],[entered_list[6],entered_list[7],entered_list[8]]]
    play_sequence = ["X", "O", "X", "O", "X", "O", "X", "O", "X"]

    print("---------")
    print("| " + matrix[0][0] + " " + matrix[0][1] + " " + matrix[0][2] + " |")
    print("| " + matrix[1][0] + " " + matrix[1][1] + " " + matrix[1][2] + " |")
    print("| " + matrix[2][0] + " " + matrix[2][1] + " " + matrix[2][2] + " |")
    print("---------")

    while not X_Win and not O_Win:
# Coordinates
    entered_coord = input("Enter the Coordinates: > ")
    # Error 1: Entered non numbers
    non_number = False
    while non_number is False:
        try:
            int(entered_coord[0])
            int(entered_coord[2])
        except ValueError:
            print("You should enter numbers!")
            entered_coord = input("Enter the Coordinates: > ")
        else:
            non_number = True
    # Error 2: Entered more than 3
    if bool(1 <= int(entered_coord[0]) <= 3) is False or bool(1 <= int(entered_coord[2]) <= 3) is False:
        print("Coordinates should be from 1 to 3!")
        entered_coord = input("Enter the Coordinates: > ")
    # Error 3: The cell is occupied
    occupied = True
    while occupied is True:
        if matrix[-int(entered_coord[2]) + 3][int(entered_coord[0]) - 1] != " ":
            print("This cell is occupied! Choose another one!")
            entered_coord = input("Enter the Coordinates: > ")
        else:
            occupied = False
    matrix[-int(entered_coord[2]) + 3][int(entered_coord[0]) - 1] = play_sequence[0]
    play_sequence.pop(0)

    print("---------")
    print("| " + matrix[0][0] + " " + matrix[0][1] + " " + matrix[0][2] + " |")
    print("| " + matrix[1][0] + " " + matrix[1][1] + " " + matrix[1][2] + " |")
    print("| " + matrix[2][0] + " " + matrix[2][1] + " " + matrix[2][2] + " |")
    print("---------")

    # case 1: X wins
    for i in matrix:
        XH_total = 0
        for j in i:
            if j == "X":
                XH_total = XH_total + 1
            if XH_total == 3:
                X_Win = True
    for i in range(3):
        if X_Win is False:
            XV_total = 0
            for j in range(3):
                if matrix[j][i] == "X":
                    XV_total = XV_total + 1
                if XV_total == 3:
                    X_Win = True
    for i in matrix:
        if X_Win is False:
            if matrix[0][0] == "X":
                if matrix[1][1] == "X":
                    if matrix[2][2] == "X":
                        X_Win = True
            if matrix[0][2] == "X":
                if matrix[1][1] == "X":
                    if matrix[2][0] == "X":
                        X_Win = True
    # case 2: O wins
    for i in matrix:
        OH_total = 0
        for j in i:
            if j == "O":
                OH_total = OH_total + 1
            if OH_total == 3:
                O_Win = True
    for i in range(3):
        if O_Win is False:
            OV_total = 0
            for j in range(3):
                if matrix[j][i] == "O":
                    OV_total = OV_total + 1
                if OV_total == 3:
                    O_Win = True
    for i in matrix:
        if O_Win is False:
            if matrix[0][0] == "O":
                if matrix[1][1] == "O":
                    if matrix[2][2] == "O":
                        O_Win = True
            if matrix[0][2] == "O":
                if matrix[1][1] == "O":
                    if matrix[2][0] == "O":
                        O_Win = True
    if O_Win is True:
        print("O wins")
    elif X_Win is True:
        print("X wins")
    elif not bool(play_sequence):
        print("Draw")
        break
