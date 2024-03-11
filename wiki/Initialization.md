**Brief description:**
	The initialization component is used to get all the information from the configuration file and region file. These files contain the layout, time limit, and refresh rate for the SimCity being built. Once these files are filled in, they are then used for the initialization of the mainList. 

**Data Storage/Maintenance:**
The mainList created from the Zone class is used inside of the initialization component. The Zone class contains x and y coordinates, zone types, and zone populations. The information read in from the file is placed into the temp Zone currZone, which is then pushed back into the mainList. The mainList then holds all of these for each input from the files so they correlate properly.

**Component Functionality:**
	There is only one function for the initialization function and it is the InitializeSim function. This function begins by asking for the configuration file from the user and confirming if the file opens correctly or not. If the file does not open the code will exit out. Once the file is open it inputs the time limit, the refresh rate, and the region file then the file is closed. The region file is then then it is opened, if the file cannot open the code will exit. The xcount, ycount, and population are initially initialized to be 0. A loop will go through each cell of the region file to get the zone type, xcount, ycount, and population to be pushed back into the mainList. The x and y counts are also increased based on the row and column of the region file inside the loop. 

[High Level Description](High Level Description)
