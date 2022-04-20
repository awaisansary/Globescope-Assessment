# Globescope-Assessment
# Problem: Trains 
Program using directional graphs to plan train rides.
# Task 
The local commuter railroad services a number of towns.  Because of monetary concerns, all of the tracks are 'one-way.' That is, a route from A to B does not imply the existence of a route from B to A. In fact, even if both of these routes do happen to exist, they are distinct and are not necessarily the same distance!

The purpose of this problem is to help the railroad provide its customers with information about the routes. In particular, you will compute the distance along a certain route, the number of different routes between two towns, and the shortest route between two towns.

# Approach 
To solve this task I decided to using the shortest path algorithm. Dijkstra's original variant found the shortest path between two nodes, but I would like to apply the most common variant fixes each single node as the "start" node and finds shortest paths from the start node to all other reachable nodes in the graph, producing a shortest-path dictionary.

Let the node at which we are starting be called the start node. Let the distance of node Y be the distance from the initial node to Y. Dijkstra's algorithm will assign some initial distance values and will try to improve them step by step.

To do this in a more technical way I create a set named visit_nodes and loop through all the nodes, initialize the visit_nodes with the start node only.
Next, I iterated through the unvisited nodes inside the visit_nodes set and took the next_node.
I further appended all neighbour nodes of the above next_node into the visit_nodes set and calculate or re-update the distances from the start node to each neighbour node and stored the minimum route inside the previous_nodes list and then stored the minimum distance inside the shortest_routes list.
Lastly, I stpped the iteration when all the visit_nodes were set and I had no more reachable nodes to add into the visit_nodes set.

I decided to solve this exercise using Node which allows me to easily turn the program into a web service in the future that can inform users about optimised train connections.

To elaborate on the chunks of code in the code file:

1. The first Djikstra's class is implemented to store all of the shortest paths and distances from every node to all reachable nodes.
2. The class Railroad receives the city-to-city railroad and their distances such as "AB5, BC4, CD8, DC8, DE6, AD5, CE2, EB3, AE7" when the Dijkstras dictionary is 
     {'A': {'B': 5.0, 'C': 9.0, 'D': 1.0, 'E': 3.0},
     'B': {'B': 9.0, 'C': 4.0, 'D': 12.0, 'E': 6.0},
     'C': {'B': 5.0, 'C': 9.0, 'D': 8.0, 'E': 2.0},
     'D': {'B': 5.0, 'C': 8.0, 'D': 16.0, 'E': 2.0},
     'E': {'B': 3.0, 'C': 7.0, 'D': 15.0, 'E': 9.0}}
   
   and installation of methods for  
    - shortest routes,
    - the distance of specific routes,
    - the number of routes from one city to another with a max number of stops,
    - the number of routes from one city to another with an exact number of stops,
    - the number of routes from one city to another with less than a specified distance.
3. The test cases to find all the distances.
    

# Graph
AB5, BC4, CD8, DC8, DE6, AD5, CE2, EB3, AE7

# Input 
A directed graph where a node represents a town and an edge represents a route between two towns. The weighting of the edge represents the distance between the two towns. A given route will never appear more than once, and for a given route, the starting and ending town will not be the same town.

For the test input, the towns are named using the first few letters of the alphabet from A to E.  A route between two towns (A to B) with a distance of 5 is represented as AB5.

# Output
For test input 1 through 5, if no such route exists, output 'NO SUCH ROUTE'. Otherwise, follow the route as given; do not make any extra stops! 

For example, the first problem means to start at city A, then travel directly to city B (a distance of 5), then directly to city C (a distance of 4). The distance of the route A-B-C. The distance of the route A-D. The distance of the route A-D-C. The distance of the route A-E-B-C-D. The distance of the route A-E-D. The number of trips starting at C and ending at C with a maximum of 3 stops. 

In the sample data below, there are two such trips: C-D-C (2 stops). and C-E-B-C (3 stops). The number of trips starting at A and ending at C with exactly 4 stops. 
In the sample data below, there are three such trips: A to C (via B,C,D); A to C (via D,C,D); and A to C (via D,E,B). The length of the shortest route (in terms of distance to travel) from A to C. The length of the shortest route (in terms of distance to travel) from B to B. The number of different routes from C to C with a distance of less than 30. In the sample data, the trips are: CDC, CEBC, CEBCDC, CDCEBC, CDEBC, CEBCEBC, CEBCEBCEBC. 

# Expected Ouptut
Output #1: 9
Output #2: 5
Output #3: 13
Output #4: 22
Output #5: NO SUCH ROUTE
Output #6: 2
Output #7: 3
Output #8: 9
Output #9: 9
Output #10: 7

# Computed Output
![image](https://user-images.githubusercontent.com/69643313/164203979-7f928309-5590-4eb4-aa69-bf35180f16a4.png)

# How to run 
Python 3 version 3.7 or above will suffice.
Python unit testing framework - Python language version of JUnit by Kent Beck and Erich Gamma.

To run make a git clone 
https://github.com/awaisansary/Globescope-Assessment.git
Run the python file on GitHub Desktop directly
Rr as I have used use Google Colaboratory to upload the python notebook (code.ipynb) to get outputs per cell.
