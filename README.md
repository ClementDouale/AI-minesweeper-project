# AI Project IA02: Minesweeper Problem with Tigers, Crocodiles, and Sharks
This project, led by Clément Douale from group 66, focuses on solving the minesweeper problem involving tigers, crocodiles, and sharks.

## Problem Description
### Variables and Clauses
- Variables per Cell: 5 (tiger, crocodile, shark, water, land)
- Total Variables for Grid: 5 * number of rows * number of columns
- Values:
- Tiger: 1
- Crocodile: 3
- Shark: 2
- Water: 4
- Land: 5

## File Writing for DIMACS
The DIMACS file writing follows a similar principle to Sudoku:

Insert basic clauses for known information about each grid cell (e.g., constraints such as not having two animals per cell, water and land in the same cell, etc.)
Insert deduced clauses based on information retrieved from the API.
Add new clauses after each discovered cell, advancing iteratively.
## Program Explanation
### Running the Program
To launch the program:

Navigate to the path containing the Python file and the client, then execute: py .\project.py.
If the program finishes the map correctly without errors or returns an error, relaunch py .\project.py for the next map.
If the program gets stuck in an infinite loop and cannot complete the map, press Ctrl+C and relaunch py .\project.py for the next map.
### Program Workflow
The program initially adds basic clauses to each grid cell.
It performs a discovery on the given API-provided cell, extracting information that is transformed into new clauses added to the existing ones.
It utilizes two lists, Case_sans_animal and AnimalPossible, to add clauses correctly and perform guesses and discoveries on the appropriate cells.
To incorporate more clauses, it uses a dictionary of Field that categorizes cells as either sea or land (0 for sea, 1 for land).
Based on the field nature, it examines neighboring cells, categorizes them, and reduces the search space by deducing information (e.g., if searching for a tiger and six adjacent cells have one land, the program determines the tiger's location without considering combinations for all six cells).
For each retrieved info in Infos, it analyzes potential animal cells, then tests various possibilities with gophersat.
If it concludes an animal's presence or absence, it guesses or discovers accordingly.
If the program cannot deduce after analyzing potential animal cells, it performs a random discovery by selecting the first cell from the list.
### Program Weakness
The program struggles to finish most maps after multiple animal discoveries or guesses when multiple animals and rows/columns exceed 5. Modifications will be attempted on Monday to address this, but participation may be limited due to in-person work commitments.

### Update for Improved Functionality
To enhance program functionality, the following updates have been implemented:

Corrected code sections where crocodile and shark were inverted.
Added a loop to launch new maps automatically after completing or failing a map.
Improved clause generation by including negative clauses while examining the neighbors of a prox_count, resulting in enhanced deductions.
