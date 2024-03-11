**Components Description**

The major components for SimCity are Initialization, Residential zone functionality, Commercial zone Functionality, Industrial zone Functionality, and region analysis. 

The initialization component reads the file given by the user and stores it. This information is used to create a main list and the time limit and steps for the simulation. Residential, commercial, and industrial components determine whether or not the population of a cell will increase based on the cell's surrounding areas and whether workers or goods are available. The region analysis component formats and outputs the main list data and gathers the population information from each zone to output.

**Class Interactions**

The class that is found within the majority of all functions in SimCity is Zone class. mainList which contains all the data for each zone is a Zone class container. It is used in the InitializeSim class to contain each x and y coordinate and zoneType of each zone when the configFile is read in. mainList is also used in ResetChanges when the function iterates through mainList and calls SetPrevChanged a Zone class function which changes all prevChanged to false.

Other functions inside of Zone class that are of note is CheckAdjZones which uses mainList and other objects to facilitate growth within each zone that meets the conditions for growth. Each timestep causes different changes and different amount of changes which increases changed. Population only increases in each types of zone. Workers only increases in residential. And workers decrease in commercial and industrial. These objects are passed by reference to main.cpp.

At the end of the program mainList is used in CalcWorkers and CalcGoods which calculates the amount of workers and goods respectively. And is used in printOutput which prints the final region, printPop which prints the final populations of each zone. And printArea which prints a specified area of the region by the user. 

**Description of Major Data Structures**

There were a few data structures used throughout the project. Lists, Classes and Objects, and Vectors and Arrays.

list<Zone> mainList is a linked list of Zone objects. This is the core data structure holding all the zones within the simulated region. Each zone object within this list represents a single cell on the map. It stores the coordinates (x, y) of each zone, stores the type of the zone (Residential 'R', Industrial 'I', Commercial 'C', Park 'P', etc.), keeps track of the zone's current population, holds information about workers and goods available in the zone, maintains the pollution level of the zone, and provides references to calculate pollution spread and zone growth conditions.

The Zone class is a class representing a single unit of the simulation map. It defines the blueprint for every zone object in mainList. It encapsulates all the relevant properties of a zone. It contains variables for storing a zone's characteristics: x and y coordinates, zoneType, numPop (population), numWorkers, numGoods, pollutionLevel, and prevChanged flag (indicates if the zone changed in the previous time step). It also houses functions to manipulate and analyze zone data: setters and getters for accessing and modifying zone properties, CheckAdjZonesR, I, C to evaluate the growth conditions of different zone types (Residential, Industrial, Commercial), setPollutionLevel() sets the pollution level based on population, getPollutionLevel() retrieves the zone's pollution level, spreadPollution() simulates outward spread of pollution from the zone.

Vectors and Arrays are used to temporarily represent the simulation map for output purposes. These structures organize the data from mainList into a grid-like format suitable for visual display. Vectors and arrays are used to store strings representing zone types or pollution levels. This data is arranged to form a visual map of the simulation. Output functions might use additional temporary arrays and variables to calculate population sums within an area or to construct a pollution map.

**System Diagram**

![UpdatedDesign.drawio](uploads/ad20b7b990d3c9a72b24d5955b57e9ac/UpdatedDesign.drawio.png)

**Component Links**

- [Initialization](Initialization)

- [Region Analysis](Analysis of the region and desired area)

- [Commercial](Commercial)

- [Industrial](Industrial)

- [Residential](Residential)