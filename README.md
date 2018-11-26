# USER-EQUILIBRIUM-SOLUTION

User equilibrium is a classical problem on the traffic flow distribution in the field of Trasportation Engineering, its main idea is: Every driver cannot reduce his travel time by unilaterally change his travel route. My professor mentioned that this is also derived from the [Nash Equilibrium](https://en.wikipedia.org/wiki/Nash_equilibrium), but I am sorry that at this time I know nothing about Game Theory.

Note: the mathematical formulars cannot be displayed correctly in the website. If you are interested in the theory part, please read the [User-Equilibrium-Solution.pdf](/README.pdf).

## PART I INSTRUCTIONS

1. Use the `create_template.py` to build a template Excel file. Before running it, you're supposed to revise the file location to where you want to save it. Remember that all the data will be read from this template later.
2. Fill in the template with your own data. Please follow the given format, or the program may not function well.  Moreover, the road network can NOT contain a loop. (Now there is no code to detect if  there exists a loop in the network graph, but I hope that I could add it soon)
3. Revise the data file (the template) location and accuracy parameters in the *main.py* as your prefer. However, do NOT let the accuracy of convex program's solution too small, or the Franke-Wolfe Algorithm can not converge.
4. Run the `main.py`, then analyze the output.

## PART II PRINCIPLES

Please read this part in [User-Equilibrium-Solution.pdf](/README.pdf).

## PART III EXAMPLES

In the file `create_template.py`, there is a good example. The graph is as follows:

![](images_folder/NETWORK.png)

The basic data of this network is given as a table:
|  LINK   | LENGTH | NO. OF LANES | FREE FLOW SPEED | CAPACITY PER LANE |
| :-----: | :----: | :----------: | :-------------: | :---------------: |
|  5 - 7  |  10.0  |      2       |       60        |       1800        |
|  5 - 9  |  10.0  |      2       |       60        |       1800        |
|  6 - 7  |  10.0  |      2       |       60        |       1800        |
|  6 - 8  |  14.1  |      2       |       60        |       1800        |
|  7 - 8  |  10.0  |      2       |       60        |       1800        |
| 7 - 10  |  10.0  |      2       |       60        |       1800        |
| 8 - 11  |  10.0  |      2       |       60        |       1800        |
| 8 - 12  |  14.1  |      2       |       60        |       1800        |
| 9 - 10  |  10.0  |      2       |       60        |       1800        |
| 9 - 16  |  22.4  |      2       |       60        |       1800        |
| 10 - 11 |  10.0  |      2       |       60        |       1800        |
| 10 - 13 |  10.0  |      2       |       60        |       1800        |
| 11 - 14 |  10.0  |      2       |       60        |       1800        |
| 12 - 15 |  10.0  |      2       |       60        |       1800        |
| 13 - 14 |  10.0  |      2       |       60        |       1800        |
| 13 - 16 |  10.0  |      2       |       60        |       1800        |
| 14 - 15 |  10.0  |      2       |       60        |       1800        |
| 14 - 17 |  10.0  |      2       |       60        |       1800        |
| 16 - 17 |  10.0  |      2       |       60        |       1800        |

We are also supposed to input the information of demand into the program:

| DEMAND | 15   |  17  |
| ------ | :--- | :--: |
| 5      | 6000 | 7500 |
| 6      | 7500 | 5250 |

Then, we can follow the instructions and run the program, then yield the output we expect.

```python
--------------------------------------------------------------------------------
TRAFFIC FLOW ASSIGN MODEL (USER EQUILIBRIUM)
FRANK-WOLFE ALGORITHM - PARAMS OF MODEL
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
LINK Information:
--------------------------------------------------------------------------------
 0 : link= ['5', '7'], free time= 10.00, capacity= 3600
 1 : link= ['5', '9'], free time= 10.00, capacity= 3600
 2 : link= ['6', '7'], free time= 10.00, capacity= 3600
 3 : link= ['6', '8'], free time= 14.10, capacity= 3600
 4 : link= ['7', '8'], free time= 10.00, capacity= 3600
 5 : link= ['7', '10'], free time= 10.00, capacity= 3600
 6 : link= ['8', '11'], free time= 10.00, capacity= 3600
 7 : link= ['8', '12'], free time= 14.10, capacity= 3600
 8 : link= ['9', '10'], free time= 10.00, capacity= 3600
 9 : link= ['9', '16'], free time= 22.40, capacity= 3600
10 : link= ['10', '11'], free time= 10.00, capacity= 3600
11 : link= ['10', '13'], free time= 10.00, capacity= 3600
12 : link= ['11', '14'], free time= 10.00, capacity= 3600
13 : link= ['12', '15'], free time= 10.00, capacity= 3600
14 : link= ['13', '14'], free time= 10.00, capacity= 3600
15 : link= ['13', '16'], free time= 10.00, capacity= 3600
16 : link= ['14', '15'], free time= 10.00, capacity= 3600
17 : link= ['14', '17'], free time= 10.00, capacity= 3600
18 : link= ['16', '17'], free time= 10.00, capacity= 3600
--------------------------------------------------------------------------------
OD Pairs Information:
--------------------------------------------------------------------------------
 0 : OD pair= ['5', '15'], demand= 6000
 1 : OD pair= ['5', '17'], demand= 6750
 2 : OD pair= ['6', '15'], demand= 7500
 3 : OD pair= ['6', '17'], demand= 5250
--------------------------------------------------------------------------------
Path Information:
--------------------------------------------------------------------------------
 0 : Conjugated OD pair= 0, Path= ['5', '7', '8', '11', '14', '15']
 1 : Conjugated OD pair= 0, Path= ['5', '7', '8', '12', '15']
 2 : Conjugated OD pair= 0, Path= ['5', '7', '10', '11', '14', '15']
 3 : Conjugated OD pair= 0, Path= ['5', '7', '10', '13', '14', '15']
 4 : Conjugated OD pair= 0, Path= ['5', '9', '10', '11', '14', '15']
 5 : Conjugated OD pair= 0, Path= ['5', '9', '10', '13', '14', '15']
 6 : Conjugated OD pair= 1, Path= ['5', '7', '8', '11', '14', '17']
 7 : Conjugated OD pair= 1, Path= ['5', '7', '10', '11', '14', '17']
 8 : Conjugated OD pair= 1, Path= ['5', '7', '10', '13', '14', '17']
 9 : Conjugated OD pair= 1, Path= ['5', '7', '10', '13', '16', '17']
10 : Conjugated OD pair= 1, Path= ['5', '9', '10', '11', '14', '17']
11 : Conjugated OD pair= 1, Path= ['5', '9', '10', '13', '14', '17']
12 : Conjugated OD pair= 1, Path= ['5', '9', '10', '13', '16', '17']
13 : Conjugated OD pair= 1, Path= ['5', '9', '16', '17']
14 : Conjugated OD pair= 2, Path= ['6', '7', '8', '11', '14', '15']
15 : Conjugated OD pair= 2, Path= ['6', '7', '8', '12', '15']
16 : Conjugated OD pair= 2, Path= ['6', '7', '10', '11', '14', '15']
17 : Conjugated OD pair= 2, Path= ['6', '7', '10', '13', '14', '15']
18 : Conjugated OD pair= 2, Path= ['6', '8', '11', '14', '15']
19 : Conjugated OD pair= 2, Path= ['6', '8', '12', '15']
20 : Conjugated OD pair= 3, Path= ['6', '7', '8', '11', '14', '17']
21 : Conjugated OD pair= 3, Path= ['6', '7', '10', '11', '14', '17']
22 : Conjugated OD pair= 3, Path= ['6', '7', '10', '13', '14', '17']
23 : Conjugated OD pair= 3, Path= ['6', '7', '10', '13', '16', '17']
24 : Conjugated OD pair= 3, Path= ['6', '8', '11', '14', '17']
--------------------------------------------------------------------------------
Link - Path Incidence Matrix:
--------------------------------------------------------------------------------
[[1 1 1 1 0 0 1 1 1 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0]
 [0 0 0 0 1 1 0 0 0 0 1 1 1 1 0 0 0 0 0 0 0 0 0 0 0]
 [0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 0 0 1 1 1 1 0]
 [0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 0 0 0 0 1]
 [1 1 0 0 0 0 1 0 0 0 0 0 0 0 1 1 0 0 0 0 1 0 0 0 0]
 [0 0 1 1 0 0 0 1 1 1 0 0 0 0 0 0 1 1 0 0 0 1 1 1 0]
 [1 0 0 0 0 0 1 0 0 0 0 0 0 0 1 0 0 0 1 0 1 0 0 0 1]
 [0 1 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 1 0 0 0 0 0]
 [0 0 0 0 1 1 0 0 0 0 1 1 1 0 0 0 0 0 0 0 0 0 0 0 0]
 [0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 0 0 0]
 [0 0 1 0 1 0 0 1 0 0 1 0 0 0 0 0 1 0 0 0 0 1 0 0 0]
 [0 0 0 1 0 1 0 0 1 1 0 1 1 0 0 0 0 1 0 0 0 0 1 1 0]
 [1 0 1 0 1 0 1 1 0 0 1 0 0 0 1 0 1 0 1 0 1 1 0 0 1]
 [0 1 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 1 0 0 0 0 0]
 [0 0 0 1 0 1 0 0 1 0 0 1 0 0 0 0 0 1 0 0 0 0 1 0 0]
 [0 0 0 0 0 0 0 0 0 1 0 0 1 0 0 0 0 0 0 0 0 0 0 1 0]
 [1 0 1 1 1 1 0 0 0 0 0 0 0 0 1 0 1 1 1 0 0 0 0 0 0]
 [0 0 0 0 0 0 1 1 1 0 1 1 0 0 0 0 0 0 0 0 1 1 1 0 1]
 [0 0 0 0 0 0 0 0 0 1 0 0 1 1 0 0 0 0 0 0 0 0 0 1 0]]
--------------------------------------------------------------------------------
TRAFFIC FLOW ASSIGN MODEL (USER EQUILIBRIUM)
FRANK-WOLFE ALGORITHM - REPORT OF SOLUTION
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
TIMES OF ITERATION : 1199
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
PERFORMANCE OF LINKS
--------------------------------------------------------------------------------
 0 : link=   ['5', '7'], flow=  5632.68, time=  18.99, v/c= 1.565
 1 : link=   ['5', '9'], flow=  7117.32, time=  32.92, v/c= 1.977
 2 : link=   ['6', '7'], flow=  6048.31, time=  21.95, v/c= 1.680
 3 : link=   ['6', '8'], flow=  6701.69, time=  39.50, v/c= 1.862
 4 : link=   ['7', '8'], flow=  5392.05, time=  17.55, v/c= 1.498
 5 : link=  ['7', '10'], flow=  6288.95, time=  23.97, v/c= 1.747
 6 : link=  ['8', '11'], flow=  5191.43, time=  16.49, v/c= 1.442
 7 : link=  ['8', '12'], flow=  6902.30, time=  42.68, v/c= 1.917
 8 : link=  ['9', '10'], flow=  1481.14, time=  10.04, v/c= 0.411
 9 : link=  ['9', '16'], flow=  5636.18, time=  42.59, v/c= 1.566
10 : link= ['10', '11'], flow=  1648.04, time=  10.07, v/c= 0.458
11 : link= ['10', '13'], flow=  6122.05, time=  22.54, v/c= 1.701
12 : link= ['11', '14'], flow=  6839.47, time=  29.54, v/c= 1.900
13 : link= ['12', '15'], flow=  6902.30, time=  30.27, v/c= 1.917
14 : link= ['13', '14'], flow=  5303.10, time=  17.06, v/c= 1.473
15 : link= ['13', '16'], flow=   818.95, time=  10.00, v/c= 0.227
16 : link= ['14', '15'], flow=  6597.70, time=  26.92, v/c= 1.833
17 : link= ['14', '17'], flow=  5544.87, time=  18.44, v/c= 1.540
18 : link= ['16', '17'], flow=  6455.13, time=  25.51, v/c= 1.793
--------------------------------------------------------------------------------
PERFORMANCE OF PATHS (GROUP BY ORIGIN-DESTINATION PAIR)
--------------------------------------------------------------------------------
 0 : group=  0, time= 109.49, path= ['5', '7', '8', '11', '14', '15']
 1 : group=  0, time= 109.49, path= ['5', '7', '8', '12', '15']
 2 : group=  0, time= 109.49, path= ['5', '7', '10', '11', '14', '15']
 3 : group=  0, time= 109.49, path= ['5', '7', '10', '13', '14', '15']
 4 : group=  0, time= 109.49, path= ['5', '9', '10', '11', '14', '15']
 5 : group=  0, time= 109.49, path= ['5', '9', '10', '13', '14', '15']
 6 : group=  1, time= 101.01, path= ['5', '7', '8', '11', '14', '17']
 7 : group=  1, time= 101.01, path= ['5', '7', '10', '11', '14', '17']
 8 : group=  1, time= 101.01, path= ['5', '7', '10', '13', '14', '17']
 9 : group=  1, time= 101.01, path= ['5', '7', '10', '13', '16', '17']
10 : group=  1, time= 101.01, path= ['5', '9', '10', '11', '14', '17']
11 : group=  1, time= 101.01, path= ['5', '9', '10', '13', '14', '17']
12 : group=  1, time= 101.01, path= ['5', '9', '10', '13', '16', '17']
13 : group=  1, time= 101.01, path= ['5', '9', '16', '17']
14 : group=  2, time= 112.45, path= ['6', '7', '8', '11', '14', '15']
15 : group=  2, time= 112.45, path= ['6', '7', '8', '12', '15']
16 : group=  2, time= 112.45, path= ['6', '7', '10', '11', '14', '15']
17 : group=  2, time= 112.45, path= ['6', '7', '10', '13', '14', '15']
18 : group=  2, time= 112.45, path= ['6', '8', '11', '14', '15']
19 : group=  2, time= 112.45, path= ['6', '8', '12', '15']
20 : group=  3, time= 103.97, path= ['6', '7', '8', '11', '14', '17']
21 : group=  3, time= 103.97, path= ['6', '7', '10', '11', '14', '17']
22 : group=  3, time= 103.97, path= ['6', '7', '10', '13', '14', '17']
23 : group=  3, time= 103.98, path= ['6', '7', '10', '13', '16', '17']
24 : group=  3, time= 103.97, path= ['6', '8', '11', '14', '17']
```

