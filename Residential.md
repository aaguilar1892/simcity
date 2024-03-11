**Brief description**

The purpose of the residential component is to calculate the population growth of the residential areas. Growth is determined by if it is adjacent to a powerline or the population of surrounding residential areas. If it fulfills any of its requisites for growth, the population and number of available workers will increase. 

**Data Storage/Maintenance**

The data for the residential zones is stored in objects of the class Zone. The Zone class has integers for coordinates of each zone placement. It also has integers for numPop and numWorkers which tracks the population and amount of workers respectively. Zone class also has a character variable to identify the type of zone, such as 'R' for residential. There is also a prevChanged variable to check if growth has already happened in the zone when iterating through. This data is stored in mainList. 

**Component Functionality**

_**Major functions used**_

CheckAdjZones(int workers, int goods, int &changed, list<Zone> &mainList) in the zone class is the major function used for this component. The function takes the integers of available workers, available goods, and amount of change in a timestep, and the list of all the zones which is contained in mainList. This function is used to initialize growth in each zone such as residential using the given variables and objects.

_**How do the functions work?**_

The CheckAdjZones(int workers, int goods, int &changed, list<Zone> &mainList) function is within a nested for loop that iterates from i to the assigned timeLimit that was specified within the configuration in the outer loop and iterates through the mainList in the inner for loop. CheckAdjZones originally takes the integers workers and goods which is initially set to zero. The function also takes mainList which is previously set by InitializeSim and has each coordinate assigned to each zone. The variable changed is also taken by CheckAdjZones. If changed is zero the loop will break.

Within the function there are six variables created. First is the boolean called power which is created for the purpose of if the adjacent zone is next to a powerline or not. Bool power is assigned as false in the beginning. Next is the four integers called adjPop1, adjPop2, adjPop3, adjPop4 which is assigned as zero initially. These four integers check to see if the adjacent zones have a population of 1, 2, 3, or 4 respectively. And the last variable assigned is prevChanged another boolean which is given false. It is used to check if the zone has already been changed or not.

After assigning each of these variables the function iterates through each object in mainList. If the object zoneType is either 'T', 'P', '#', '-', 'R', 'I', or 'C' then the function enters a for loop because it means that the zone is adjacent. Then it goes through the conditions, such as if the zone is a 'T' zone or the current population, then if it is 'T' it will be assigned as true for power and for its respective population adjPop will increase.

Next it checks the zone type and goes into the respective if statement, such as if(zoneType == 'R'). It then checks each growth condition such as if a residential zone is next to a powerline when the population is zero and prevChange is false. If so then the population increase as well as number of available workers. If the population is zero and one or more adjacent to a zone with a population of at least one and prevChange is false then the population increase as well as number of available workers. If the population is one and two or more adjacent to a zone with a population of at least one and prevChange is false then the population increase as well as number of available workers. If the population is two and four adjacent to a zone with a population of at least two and prevChange is false then the population increase as well as number of available workers. If the population is three and six or more adjacent to a zone with a population of at least three and prevChange is false then the population increase as well as number of available workers. If the population is four and eight or more adjacent to a zone with a population of at least four and prevChange is false then the population increase as well as number of available workers. Else nothing happens.

_**How data moved/transformed?**_

If any of the conditions for residential growth is true then numPop and numWorkers increases by one because as one person is added to the population another available worker also becomes available. Changed also increase by one for the timestep. And prevChanged is changed to true as the zone has been visited.

**_How data read in & output?_**

Zone::CheckAdjZones(int workers, int goods, int &changed, list<Zone> &mainList) is a void function thus not returning anything to main.cpp. Instead each argument is passed by reference. All data that comes from the arguments is either assigned in main.cpp or InitializeSim function.

[High Level Description](High Level Description)