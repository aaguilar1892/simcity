**Brief Description**

The commercial component's purpose is to determine the growth of the city's commercial zones based on a variety of factors such as whether or not the zone is next to a powerline, the population of neighboring zones, and whether or not there are enough available goods and workers for the zone to grow.


**Data Storage/Maintenance**

The data for all zones, including commercial zones, is stored in objects of the Zone class, which are stored inside the list of all zones, mainList. An individual Zone object is created for each zone read into the simulation.

The Zone class includes integer variables, x and y, for the x and y coordinates of the zone, a character variable, zoneType, representing the type of zone (commercial is represented by 'C'), an integer variable, numPop, for the zone's population, integer variables, numWorkers and numGoods, for the number of available workers and goods, and a boolean variable, prevChanged, for whether the zone already experienced growth during the current time step.


**Component Functionality**

**_Major Functions Used_**

The function used to analyze and determine the growth of commercial zones is the Zone class void function, CheckAdjZonesC(int &workers, int &goods, int &changed, list<Zone> &mainList), which takes as arguments integer variables workers and goods, for the total number of available workers and goods in the city, an integer variable, changed, representing the number of total number of times zones grew during the current time step, and a list of Zone objects, mainList, that contains all of the zones in the city.

**_How it Works_**

The function is called during each time step for every zone in mainList, and first checks for any characteristics of adjacent zones that could fulfill growth conditions for the zone.

The characteristics found in possible growth conditions include whether the zone is adjacent to a powerline (represented by the boolean variable, power) and the number of adjacent zones with a population of at least one, two, three, or four, (represented by the integer variables, adjPop1, adjPop2, adjPop3, and adjPop4, respectively). The variable power is initialized to false, and the adjPop integers are initialized to zero.

The function iterates through each zone in mainList to find adjacent zones that are equal or differ by only one in their x and y coordinates but do not have both the same x-coordinate and the same y-coordinate.

If the zone is adjacent, then the function checks if the adjacent zone's type is 'T' (for a powerline). If so, the power variable is marked true.

It also checks the population of the adjacent zone. If the population is greater than or equal to four and the zone has not already been changed in the current time step, or if the zone has been changed, but the population before the change was greater than or equal to four, then the variable adjPop4 is increased by one. The same process is repeated for the other adjPop variables, but replacing the four population with three, two, and finally one.

Next, the function uses these variables to check whether the zone fulfills one of its growth conditions. 

These growth conditions are if either the zone is adjacent to a powerline, its population is zero, and there is at least one worker and good, or if the zone's population is zero, it is adjacent to at least one zone with a population of at least one, and there is at least one worker and good, or if the zone's population is one, it is adjacent to at least two zones with a population of at least one, and there is at least one worker and good.

**_How Data Transformed_**

If any of these conditions are true, then the zone's population (numPop) increases by one, the number of total goods (goods) decreases by one, the number of workers in the zone (numWorkers) decreases by one, the number of changes during the time step (changed) increases by one, and the zone is marked as changed for the current time step (prevChanged set to true).

**_How Data Read In and Output_**

The void function CheckAdjZonesC does not return any value, but each of its arguments are pass by reference and thus update the corresponding variable in main.cpp.

[High Level Description](High Level Description)