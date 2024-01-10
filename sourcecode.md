# Cricket Game by w.v.p.s.sriraj, dm me in insta for more info!
print(""" ~~~~ Computer Cricket Saga ~~~~  
RULES AND REGULATIONS: 
1. You have to select any random number between 1 to 6 (1 and 6 included). 
2. The computer will also select a number respectively. 
3. While batting, if the number selected by you and the computer is the same, then you will lose your wicket. If the number selected by you and the computer is different, then your number will add to your runs. 
4. While bowling, if the number selected by you and the computer is different, then the computer's number will add to its runs. If the number selected by you and the computer is the same, then the computer will lose its wicket.
5. Each player will get 5 wickets and 3 overs (18 balls) for batting and bowling. 
6. The innings will end after either the five wickets fell or the overs end. 
7. The player with maximum runs wins.
8. While choosing the toss, if u typed any other word except heads or tails or did any spelling mistake, the system will take default and will win the win the toss which eventually lead u losing the toss.
9. All the best guys :) 
""") 

print("\n- Let's Start!! -")

import random

# Toss
print("\nTime for the toss!")
toss = input("Choose heads / tails: ").lower()

random_toss = random.randint(1, 2)
random_opt = random.randint(1, 2)
u_opt = 0
c_opt = 0

if random_toss == 1 and toss == "heads":
    print("\nYou won the toss")
    # In random_toss (1 = Heads) and (2 = Tails)
    # In random_opt (1 = bat) and (2 = ball)
    u_opt = input("Choose bat or ball: ").lower()
elif random_toss == 2 and toss == "tails":
    print("\nYou won the toss")
    u_opt = input("Choose bat or ball: ").lower()
else:
    print("\nYou lost the toss :( ")

if random_opt == 1:
    c_opt = "bat"
    print("Computer chooses to", c_opt)
elif random_opt == 2:
    c_opt = "ball"
    print("Computer chooses to", c_opt)

# First Innings
print("\n--------------- First Innings Starts ---------------")
runs_1 = 0
wickets_1 = 0
balls_1 = 0

while wickets_1 != 5 and balls_1 != 18:
    u_choice = int(input("\nChoose any number from 1 to 6: "))
    c_choice = random.randint(1, 6)

    if u_choice < 1 or u_choice > 6:
        print("\nChoose a value from 1 to 6.")
    else:
        print("Player's choice: ", u_choice, "\nComputer's choice: ", c_choice)
        if u_choice == c_choice:
            wickets_1 += 1
        else:
            if u_opt == "bat" or c_opt == "ball":
                Bat_first = "You(player)"
                Ball_first = "Computer"
                runs_1 += u_choice
            elif u_opt == "ball" or c_opt == "bat":
                Bat_first = "Computer"
                Ball_first = "You(player)"
                runs_1 += c_choice
            print("\nScore =", runs_1, "/", wickets_1)
            balls_1 += 1

        if balls_1 == 6:
            print("End of Over 1!")
        elif balls_1 == 12:
            print("End of Over 2!")
        elif balls_1 == 18:
            print("End of over 3!")

        print("Balls remaining: ", 18 - balls_1)

print("\n--------------- End of Innings ---------------")
print("\nFinal Score:")
print("Runs =", runs_1)
print("Wickets =", wickets_1)

print("\n", Ball_first, "needs", runs_1 + 1, "runs to win :)")

# Second Innings
print("\n--------------- Second Innings Starts ---------------")
runs_2 = 0
wickets_2 = 0
balls_2 = 0

while wickets_2 != 5 and balls_2 != 18 and runs_2 <= runs_1:
    u_choice = int(input("\nChoose any number from 1 to 6: "))
    c_choice = random.randint(1, 6)

    if u_choice < 1 or u_choice > 6:
        print("\nChoose a value from 1 to 6.")
    else:
        print("Player's choice: ", u_choice, "\nComputer's choice: ", c_choice)
        if u_choice == c_choice:
            wickets_2 += 1
        else:
            if Bat_first == "Computer":
                runs_2 += u_choice
                Bat_second = "You(player)"
            elif Bat_first == "You(player)":
                runs_2 += c_choice
                Bat_second = "Computer"

            print("\nScore is =", runs_2, "/", wickets_2)
            balls_2 += 1

            if balls_2 == 6:
                print("End of Over 1!")
            elif balls_2 == 12:
                print("End of Over 2!")
            elif balls_2 == 18:
                print("End of over 3!")

        if runs_2 <= runs_1 and balls_2 <= 17 and wickets_2 != 5:
            print("RRR:", runs_1 - runs_2 + 1, "runs needed from", 18 - balls_2, "balls.")

print("\n---------- End of the Innings!!!")
print("\nFinal Score:")
print("Runs =", runs_2)
print("Wickets =", wickets_2)

# Result of the Match
print("\n~~~~ Result!! ~~~~")

if runs_1 > runs_2:
    if Bat_first == "You(player)":
        print("\nCongrats!! You(player) won the Match by", runs_1 - runs_2, "runs!!! :)")
    else:
        print("\nHard luck! The Computer won the Match by", runs_1 - runs_2, "runs!!!")
elif runs_2 > runs_1:
    if Bat_second == "You(player)":
        print("\nCongratulations! You(player) won the Match by", wickets_2, "wickets.")
    else:
        print("\nHard luck! The Computer won the Match by", wickets_2, "wickets :( ")
else:
    print("OMG! This Match's a Tie!", "\nNo one Wins.")
