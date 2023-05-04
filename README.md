Download Link: https://assignmentchef.com/product/solved-csci1100-computer-science-1-homework-5-wandering-trainer
<br>
<h1>Part 1: Wandering Trainer</h1>

A pokemon trainer is placed in the middle of a grid that is <em>M </em>rows tall and <em>N </em>columns wide. These values are read into the program by asking the user. The user must also be asked for a probability <em>p </em>that must be great than 0<em>.</em>0 and less than 1<em>.</em>0, but will generally be relatively small. The reason for the probability is explained below. You may assume all input is correct. The upper left corner of the grid is location (0<em>,</em>0), while the bottom right corner is location (<em>M </em>− 1<em>,N </em>− 1). The trainer starts out at location (<em>M//</em>2<em>,N//</em>2). At each turn, the trainer will take a step in a random direction and look for a pokemon.

The program must simulate random movements of the trainer. As in HW 4, Part 3, the trainer can can only move in a straight line to the North (decreasing row), South (increasing row), East (increasing column), and West (decreasing column) one step per turn. After taking a step, the trainer will have a <em>p </em>probability of finding a pokemon on that spot. To manage this operations, we will use:

random.randint(0, 3) random.random()

Each time it is called random.randint(0, 3) returns one of 0, 1, 2 or 3. If the value return is: 0 – The trainer moves North one step

<ul>

 <li>– The trainer moves South one step</li>

 <li>– The trainer moves East one step</li>

 <li>– The trainer moves West one step</li>

</ul>

Once the trainer moves, random.random() is called to generate a floating number between 0 and 1. If the value returned is less than <em>p </em>the trainer finds a pokemon on the current spot. Otherwise, no pokemon is found. Order is important, in every turn make sure you generate the direction <strong>(randint(0, 3)) </strong>first and then the capture probability, (<strong>random)</strong>! The trainer should continue to make these random steps until 250 time steps (turns) have passed. As in HW 4, the trainer cannot go past the boundaries of the grid. It the trainer tries to move past the boundary, for example, by trying to go North when the <em>row </em>coordinate is 0, the trainer just stays at the same location and searches again for a pokemon.

To solve part 1 your program must report the position of the trainer and the number of pokemon collected. Once the simulation ends you must output the final position and the total number of pokemon collected.

<strong>Important Details:</strong>

<ol>

 <li>In order for everyone to have the same output we must <em>seed </em>the random number generator. After you read the user input, but before the first time you call one of the random functions, you must include the following code</li>

</ol>

seed_value = 10*M + N

random.seed(seed_value)

The seed ensures that the random number generator gives the same sequence of values for the random calls. For us, that means that we can compare your output to our output and expect to get the same sequence of movements and captures. To see more interesting behavior when testing your program, you might want to comment out the call to the seed function; just be sure to put it back in before you submit!

<ol start="2">

 <li>You <strong>MUST </strong>write and use</li>

</ol>

def move_trainer( position, bounds, prob):

’’’

position is the current (row, col) position of the trainer, passed as a tuple bounds is the max (rows, cols) on the grid, again as a tuple prob is the probability p that a pokemon will be found at the current position

’’’

which moves the trainer for one time unit, checking for a pokemon at the resulting location. The function must return a tuple containing in order, the new position (row, col) and 1 if a pokemon was found this turn, or 0 otherwise. Your main code must then call this function in some kind of loop and use the results to track the pokemon and decide what to output. Do <strong>not </strong>call the random.seed function inside the move_trainer function.

<ol start="3">

 <li>In move_trainer you <strong>must </strong>make the calls to random.randint(0, 3) and random.random() in the correct order and exactly once per turn. Test the values returned to decide what move to make and if a pokemon is captured.</li>

</ol>

<strong>Additional Notes:</strong>

<ol>

 <li>Turns should run from 1 to 250</li>

 <li>In each turn:

  <ul>

   <li>Take a step and check for a caught pokemon using move_trainer</li>

   <li>Every 20 turns print the trainer’s position and number of pokemon caught since the last report</li>

  </ul></li>

 <li>At the end, output the final number of time steps, the final position, and the total number of pokemon found. See examples below for details.</li>

</ol>

<strong>Example 1:</strong>

Enter the integer number of rows =&gt; 40 40

Enter the integer number of cols =&gt; 46

46

Enter the probability of finding a pokemon (&lt;= 1.0) =&gt; 0.15

0.15

Time step 20: position (24, 23) pokemon caught since the last report 2

Time step 40: position (28, 15) pokemon caught since the last report 4

Time step 60: position (32, 17) pokemon caught since the last report 2

Time step 80: position (30, 21) pokemon caught since the last report 3

Time step 100: position (26, 17) pokemon caught since the last report 6

Time step 120: position (27, 18) pokemon caught since the last report 4

Time step 140: position (29, 20) pokemon caught since the last report 4

Time step 160: position (33, 18) pokemon caught since the last report 3

Time step 180: position (31, 22) pokemon caught since the last report 1

Time step 200: position (34, 25) pokemon caught since the last report 2

Time step 220: position (34, 23) pokemon caught since the last report 6

Time step 240: position (35, 26) pokemon caught since the last report 3 After 250 time steps the trainer ended at position (36, 25) with 40 pokemon.

<strong>Example 2:</strong>

Enter the integer number of rows =&gt; 100 100

Enter the integer number of cols =&gt; 300

300

Enter the probability of finding a pokemon (&lt;= 1.0) =&gt; 0

0.0

Time step 20: position (51, 155) pokemon caught since the last report 0

Time step 40: position (48, 154) pokemon caught since the last report 0

Time step 60: position (56, 156) pokemon caught since the last report 0

Time step 80: position (55, 149) pokemon caught since the last report 0

Time step 100: position (53, 151) pokemon caught since the last report 0

Time step 120: position (54, 152) pokemon caught since the last report 0

Time step 140: position (57, 157) pokemon caught since the last report 0

Time step 160: position (53, 155) pokemon caught since the last report 0

Time step 180: position (51, 145) pokemon caught since the last report 0

Time step 200: position (54, 144) pokemon caught since the last report 0

Time step 220: position (57, 145) pokemon caught since the last report 0

Time step 240: position (58, 142) pokemon caught since the last report 0 After 250 time steps the trainer ended at position (58, 142) with 0 pokemon.

<strong>Example 3:</strong>

Enter the integer number of rows =&gt; 10 10

Enter the integer number of cols =&gt; 30

30

Enter the probability of finding a pokemon (&lt;= 1.0) =&gt; 1

1.0

Time step 20: position (4, 14) pokemon caught since the last report 20 Time step 40: position (5, 9) pokemon caught since the last report 20

Time step 60: position (5, 11) pokemon caught since the last report 20

Time step 80: position (6, 10) pokemon caught since the last report 20

Time step 100: position (9, 1) pokemon caught since the last report 20

Time step 120: position (9, 0) pokemon caught since the last report 20

Time step 140: position (9, 2) pokemon caught since the last report 20

Time step 160: position (5, 3) pokemon caught since the last report 20

Time step 180: position (9, 6) pokemon caught since the last report 20

Time step 200: position (9, 3) pokemon caught since the last report 20

Time step 220: position (6, 8) pokemon caught since the last report 20

Time step 240: position (1, 9) pokemon caught since the last report 20

After 250 time steps the trainer ended at position (0, 8) with 250 pokemon.

<h1>Part 2: Gathering Data About the Wandering Trainer</h1>

Thus far, we have only considered a single case of running the pokemon simulation, but simulations are typically run over and over again and statistics are gathered about the results of the runs. So, in this second part of the assignment your program will need to repeat the simulation a user-specified number of times, and output several summary statistics:

<ol>

 <li>An output of the grid showing the number of times that a pokemon was caught in each position.</li>

 <li>The minimum and maximum number of pokemon caught in a single simulation and the simulation number (from 1 to the number of simulations run) at which these occurred.</li>

 <li>The total number of pokemon caught across all simulations.</li>

 <li>The maximum number of pokemon caught at <em>any </em>position as an integer and as a percentage of the total pokemon caught.</li>

 <li>The minimum number of pokemon caught at <em>any </em>position as an integer and as a percentage of the total pokemon caught.</li>

</ol>

<strong>A Counting Grid: </strong>You must create a list of lists of counts for the number of times the trainer catches a pokemon in each cell of the grid. Here are two examples to help you. The first example shows an easy way to initialize the grid to have M rows and N columns:

count_grid = [] for i in range(M): count_grid.append( [0]*N )

The second example illustrates counting the number of occurrences of the numbers 0 through 9 using the random number generator (without using the seed function):

import random

num_trials = 2500 counts = [0]*10 for i in range(num_trials): digit = random.randint(0,9) counts[digit] += 1

print(<sup>’</sup>Occurrences and percentages:<sup>’</sup>) for i in range(10):

print(“{:1d}: {:4d} {:4.1f}”.format(i, counts[i], 100.0*counts[i]/num_trials))

<strong>Important details:</strong>

You must <strong>make </strong>use of the move_trainer function from part 1. You can copy and paste it into your hw5Part2.py file.

Next you <strong>must </strong>write and test a function called

def run_one_simulation( grid, prob ):

’’’

runs the simulation and keeps track of the number of pokemon caught on each space in the grid. prob is the probability a pokemon will be caught at each turn

’’’

that starts the trainer in the center of the grid, and runs one full simulation of the trainer until it reaches the maximum number of time steps. At the end, it returns the number of pokemon caught during the simulation. Each time step has two phases. In the first phase, the trainer moves and during the second phase the trainer tries to catch a pokemon. This is exactly your move_trainer function from Part 1 and run_one_simulation should call move_trainer once per time step to move the trainer and capture pokemon. The results should be tracked and recorded in grid. For instance, suppose that move_trainer returns (row, col) as the trainer position and 1 as the number of pokemon caught that turn. Your code should increment grid_count[row][col] by one to account for the captured pokemon. You <strong>must </strong>have run_one_simulation in your program, but you may change its parameters as you wish. For example, you could pass M and N — the number of rows and columns — although you do not need to because you can compute the values from the grid_count list of lists.

Do <strong>not </strong>call random.seed from inside run_one_simulation. It will cause the random number generator to start over for each simulation and so your results will be the same for each simulation.

Each time you call run_one_simulation the trainer should start in the center of the grid.

We <em>suggest </em>that you write a function to extract and print the statistics of the grid in order to avoid cluttering the code in the main body of the program.

At the end of the simulation, you may want to have run_one_simulation return the number of pokemon caught during that run. This will help with tracking the minimum and maximum number of pokemon caught per simulation.

Finally, here is an example that illustrates the output and formatting we are expecting.

Enter the integer number of rows =&gt; 18 18

Enter the integer number of cols =&gt; 16

16

Enter the probability of finding a pokemon (&lt;= 1.0) =&gt; 0.4

0.4

Enter the number of simulations to run =&gt; 100

100

20 21 18 17 21 28 21 34 26 22 27 32 20 21 26 37

15 23 18 19 17 19 21 39 24 21 20 37 38 41 40 47

24 29 27 19                                 8 25 24 32 23 37 38 36 30 30 36 33

9 18 18 20 19 33 34 26 19 30 37 32 31 30 23 41

12 18 14 24 31 38 31 22 22 28 49 36 31 28 36 36

20 24 20 29 30 36 34 33 32 42 47 43 24 34 28 36

20 19 18 26 29 19 32 44 40 37 37 46 35 28 33 46

20 34 29 16 23 27 41 45 59 50 58 35 31 32 28 43

23 26 20 31 25 29 43 60 83 61 47 36 36 28 25 34

19 30 31 23 23 30 46 59 73 63 57 39 28 36 24 27

25 37 19 22 34 31 39 64 71 66 61 36 29 35 37 19

46 39 30 25 36 35 36 44 46 57 38 45 36 32 33 28

35 38 27 30 35 51 47 47 48 54 54 58 42 41 59 45

43 28 32 28 35 38 48 38 56 40 58 56 40 27 44 47

27 28 32 34 45 54 54 38 39 30 32 35 43 45 50 46

31 35 37 28 33 39 42 42 31 35 29 48 40 52 41 50

31 29 36 34 35 36 36 27 22 26 39 44 40 40 48 49

34 35 33 25 27 29 28 25 35 26 46 52 43 41 47 44

Total pokemon caught is 9951

Minimum pokemon caught was 81 in simulation 61

Maximum pokemon caught was 125 in simulation 52

Max number of pokemon caught on a space is 83 which was 0.83% of all pokemon caught

Min number of pokemon caught on a space is 8 which was 0.08% of all pokemon caught

And one more showing a potential failure case:

Enter the integer number of rows =&gt; 15 15

Enter the integer number of cols =&gt; 12

12

Enter the probability of finding a pokemon (&lt;= 1.0) =&gt; 0

0.0

Enter the number of simulations to run =&gt; 10 10

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

0       0       0       0       0       0       0       0       0       0       0       0

Total pokemon caught is 0

Minimum pokemon caught was 0 in simulation 1

Maximum pokemon caught was 0 in simulation 1

Max number of pokemon caught on a space is 0

Min number of pokemon caught on a space is 0

In terms of formatting, each of the output values in the grid is formatted with {:4d}. You can either generate each row as a string and print it out, or you can use the sep= and end= values of the print statement to control the formatting.

<h1>Some notes on debugging</h1>

This is your most complex homework to date, so here are some suggestions for debugging:

We are asking you to use large grids, 250 iterations per simulation, and for Part 2 a large number of iterations. This is too much to debug easily. Start small

<ul>

 <li>Use Part 1 to get move_trainer working and to test it thoroughly. Step through it in the debugger, make sure all paths are selected and make sure that the positions of the trainer after each move are right. It should only take you a few times through the loop.</li>

 <li>Use a small grid, eg. 5<em>x</em>6 to check the behavior of the trainer as it walks up to the boundary. Does it go too far? Does it stop short? Make sure it works from all directions moving N, S, E, and W.</li>

 <li>If you think your code is working correctly, but you are not matching our output, print out and check your seed first, and then check the number of random calls (random and randint) and the order you are making them. You will only need one randint call and one random call per iteration. The seed function should only be called <strong>once </strong>in any program.</li>

 <li>Use special values of the probability to simplify testing. For example, a probability of 1 should capture a pokemon every turn. 0 should capture no pokemon</li>

</ul>

In Part 2, use functions and debug them separately.

Start out small. In Part 2 use a small grid, a small number of turns per simulation, and a small number of simulations. For example, with a 5<em>x</em>6 grid, 5 turns per simulation, and 2 simulations; you can easily trace your program execution using the debugger or print statements to verify execution.