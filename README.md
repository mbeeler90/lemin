# Lem-in

## About
The task in this project is to move ants from a start point to an end point of an ant colony. The ant colony consists of a random number of rooms that are randomly connected to each other. The goal is identify paths on which the ants can walk from the start to the end room, so that all ant move from the start to the end room in as few turns as possible. 

The constraints are:
- An ant can only move one room per turn.
- Each room (except start and end) can max contain one ant.

## Stragegy
We use the Edmonds-Karp algorithm with the following specifications to solve the problem:
- Each room (except start and end) is split into an in and out room. From the in room, ants can only move to the out room. From the out room, the ants can move to the connected rooms.
- All connections between rooms (incl. between in and out room) have a capacity of 1 (direction in which the ants can move) and 0 (in the reverse direction).
These conditions ensure that there is never more than one ant in a room at any given time.

The algorithm then finds the best solution:
1. Find the shortest aughmented path.
2. If no valid path was found, exit algorithm, otherwise continue with step 3.
3. Change capacity of connections and reverse connections along the augmented path form 1 to 0 and 1 to 0 respectively.
4. Caluculate the number of turns required to move all ants from the start to the end based on current combination of paths.
5. Set required moves as best solution if it is lower the current best solution
6. Repeat from step 1.

## Compiling
Run `make` to compile an executable called fillit.

## Usage
`./lem_in < ./maps/[MAP]`
