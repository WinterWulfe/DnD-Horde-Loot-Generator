# DnD-Horde-Loot-Generator
A Python program designed to streamline the loot distribution process when your players find a treasure horde. Also includes an Individual Treasure Generator.

User Guide
	There is not much setup or preparation necessary for this program.  It was designed to be something that could be fit into a .zip file along with all the data and metadata necessary for it to be properly run. A very important part of the program is the raw text files that should be found alongside the .py file.  They must be located within the same directory as the executing program.  Also, their names are immutable.  The program specifically searches for text files of the names that have been given.  Changing the names will almost certainly cause the data retrieval aspects of the program to perform improperly.  
	The program does not have an executable file and must be run in the Python shell manager.  Nonetheless, it was designed for ease of use.  The program is heavily user interactive but requires very little complex input.  The entire program can be navigated with only numbers.  During times when the user is expected to provide input, there is expected input redundancy put in place to allow the user to navigate the program more reliably and with fewer stops due to incorrect input.  There is also exception handling put in place to prevent crashes from incorrect input.  
	So long as all the text files and the executable are in the same directory at execution time, the program should perform properly.  If the user wishes to, at any time, browse the items found within the item tables, they can do so at any time by simply opening up the raw text files.  

Developer Guide
The program begins by initializing the dictionaries necessary for the proper processes of the program.  Shortly afterwards, data from the raw text files are loaded and set into the dictionaries corresponding to the names of the files.  Every text line within the text files occurs in the form “number: item.”  The program reads these files and uses the colon “:” symbol as a demarcation unit.  All data to the left of the colon (the number) is made into a key for the dictionary.  All data to the right is made into the value for the dictionary.  Key/Value pairs are continuously generated and stored into the associated dictionary until the file ends, after which the file closes.
Once the dictionaries have been populated, the two classes within the program, “Individual” and “Horde” are described and provided initialization criterion.  Both classes serve the purpose of summarizing the data generated in the “Random Generation” module of the program.  There are two submodules within “Random Generation:” Individual Encounter and Horde Encounter.  The first submodule involves randomly generating treasure for small encounters between individual enemies that might be carrying treasure on their person, which the players can then take once the enemies have been defeated.  Individual treasure does not strictly allow players to roll on treasure tables, and as such the only values found within the class “Individual” are the values for copper, silver, electrum, gold, and platinum, the standard currencies of the game and thus the only real items of value that players should expect someone to be carrying on their person.  Horde encounters, however, also allows players to roll for various forms of treasure, such as valuable art objects, precious gemstones, and magical items that can help them in their quest.  However, these new categories of treasure require that their data types actually be lists instead of integer values since all of these items have descriptors and/or names associated with them that cannot be adequately translated by simple monetary values.  Even if players may not receive all of the items mentioned above in a single encounter, the Horde class is given potential values for all the types of currency and treasure listed above.  
The functions are separated in Python comments by which module they are used in.  The functions necessary for the Manual Input operations are separated from the functions necessary for Random Generation operations.  Much of the code necessitates that the user navigate through various areas, even in the case of Random Generation.  However, the operations of the Manual Input module are exclusively reliant on the user for item and treasure generation.  As such, for the sake of simplicity, much of the code in any of the functions for the Manual module look very similar to each other since they all simplify down to calls for input, with resulting output either being navigation through the code or the generation of treasure.  If the user does generate treasure, they do so by typing in a number within the bounds of the dictionary that they are receiving an item from.  Each item within the dictionary has an associated key in the form of an integer.  If that integer is called, the corresponding value – treasure – is given as output.
This same basic logic also follows for the Random Generation module except that the user only gives very minimal input, usually in the form of a difficulty spectrum.  The user specifies the difficulty of the battle that the players just engaged in.  Battles of greater difficulty provide greater rewards, and the real difficulty of the battle is specified in the Challenge Rating (CR) of the battle.  However, anyone who would actually be using this program would almost certainly already know how to calculate CR difficulty, so providing a method for calculating it in this program would be outside its scope.  If the players engaged in a small battle between individual people, they roll on the “Individual Treasure” table, which the program provides.  If the players engage in a massive battle with an army and/or any massive creature that voraciously hordes treasure (like dragons), then they instead roll on the “Horde Treasure” table.  This is easily one of the most exciting moments when playing the game, just like Christmas Day is for a bunch of children.  The prospect of lots of money and new toys and tools to play with is quite exciting for players, but the entire process takes a decent amount of time to completely figure out without this program.  It requires that the players roll a large number of dice to randomly determine what they find.  This program streamlines the necessary dice rolls, thus allowing Treasure Horde loot to be generated much more quickly.
The Horde Treasure and Individual Treasure sections of the program are very similar to the Manual Input section of the program in that most of the actual determination of what items are received comes from the retrieval of values within dictionaries according to a given number key.  However, when rolling for Treasure, there are a number of additional rules that must be considered that unfortunately cannot be easily transcribed into a text file like the item tables can.  Thus, many of these rules are coded inherently into the program itself.  In fact, the largest section of the program comes from the hard coding of these rules into the treasure generation process.
Should the user wish to customize the potential treasure drops that their players will receive, they can easily go inside the raw text files and alter them to suit their needs.  However, please be sure to keep in mind that the program requires the text data be in the format of “number: item.”  If this format is disrupted, or if a user accidentally creates two of the same key within a dictionary, the program may not run properly or the dictionary may not contain all the values that it should.  If the user feels confident enough to enter into the code and modify the item generation scheme within the Random Generation module, they can certainly feel free to do so.  It is pretty obvious where it is located as it takes up roughly half of the entire program.  However, keep in mind that any dramatic alterations may cause the program to crash if done improperly, so it is always recommended to have a backup just in case.
