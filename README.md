# Project A3: Path Planning

Due Date: November 28, 2022

In this lab, you will implement Dijkstra's Algorithm to find the shortest path given a source and destination(s) in a predefined map. This is a pair assignment (teams of 2 max). Make changes and push to this repository to complete the project.

## Environment Setup
The only requirement for this lab is C++11. You can choose to work locally if you wish. 

## Project Structure
The project directory is structured as follows:

- Map/ : Contains the predefined maps
- Makefile : To compile your program
- src/ : Source files (main.cpp iis provided, you must add the remaining)
- include/ : For common header files

## Project Details

Your task is to complete a Dijkstra's implementation in C++. You program must take in CLI the map, a source and destination(s) and output the shortest path found. Note that only one source can be passed but multiple destinations to the program.

You must complete `main.cpp` and also create two further classes (with their associated source files) called `GMap` and `DijkstraSP`. The details of these class implementations will be discussed.
 ***Important:*** You are ***not*** allowed to use any existing Dijkstra's code, you must develop the code yourselves. You are also not allowed to import <algorithms>. Failure to comply with these rules will yield you 0 points.

### Makefile
Similar to your prior project, you must create your own Makefile. There is no need to link any external libraries. The only requirements for your Makefile is to use C++11, compile with `-Wall`, `-Werror`, and have a `clean` rule to remove your executable. Please name your executable `dijkstraSP`

### Map Structure
You are provided a sample map in `Map/bay.txt`. The first two entires are the total vertices and edges. Following that is the edge list tthat defines our map as a graph (non-directional).
The map will be a txt file following the following structure:
```
EEC174AY Map
<Vertices> <Edges>

<Vertex1> - <Vertex2> : <Edge_Weight>
```

So, for instance the in `bay.txt`, the first few entires look like this:
```
EEC174AY Map
13 19

Mill Valley - San Francisco : 14.8
San Francisco - Oakland : 12.1
```

Hence, there is an edge of weight 14.8 between vertices "Mill Valley" and "San Francisco". Note that the map is considered valid if it has "EEC174AY Map" as its first entry.

### `GMap` Class
You must implement a class called `GMap`. This class must be able to take in the provided map and read it into a suitable graph representation. There are two ways to represent graphs: Adjacency Matrix and Adjacency List. The matrix representation is easier to implement.
To receive full credit, you must use an Adjacency List to represent your graph. If you use an Adjacency Matrix, you will only receive partial credit. You will find this breakdown in the Evaluation section.
Your class should have a function to read the Map and store its contents into the representation you chose. You must also provide a function that will print your graph (as an Adjacency List or Matrix depending on which one you chose).

### `DijkstraSP` Class
You must implement a class called `DijkstraSP`. This class will take in your graph representation from `GMap`, your source and destination(s), then perform Dijkstra's algorithm to find the shortest path. Your class must be able to identify the shortest path as well as the total distance (edge weight) for that path.

### Main
The main file must read in the CLI, and perform a thorough error checking on them. The basic steps you should perform in `main.cpp` are:

- Check CLI
- Read input map and create your Adjacency List/Matrix using `GMap`
- Feed your Adjacency List/Matrix, source and destination into Dijkstra's Algorithm to determin shortest path using `DijkstraSP`
- Print the shortest path on terminal

Here is how your program must be used:
```
bin/dijkstraSP <map> <source> <destination(s)>
```

We can pass in just one source and one destination or one source and multiple destinations. For instance using `map1.txt` we can have:
```
bin/dijkstraSP map1.txt A E,B
```

Please note that destinations must be passed in with commas (',') without any spaces. If a space is used between destinations, the program will only recognize the dirst destination. For instance if we use `map1.txt`, source = A and destination = E,C the output will be:
```
A -> E (1)
A -> B -> C (3)
```

Where we have (for each destination): `<source> -> <vertex1> -> ... -> <destination> (<total_distance>)`

## Evaluation

The TAs executable is provided (`ref/dijksp_kartik`). You ***must*** use it to test your code. You will be graded against this executable. Please ensure that the outputs match ***exactly*** since your correctness will be graded using an autograder script. You are provided `map1.txt` and `bay.txt` to test your code.

### Grade Breakdown

- Program Correctness: 60
- Program Speed: 20
- Style, Comments, & Implementation: 10
- Interactive Grading: 10

Avoid collaboratation or sharing code. You also must implement Dijkstra's and your graph representation on your own. If any external references are used, please make sure to cite them. This includes sources such as GeeksforGeeks, Stackoverflow, textbooks, etc. However, you are ***NOT*** allowed to directly use/copy any existing solution code on github. To avoid consequences, please do not violate this.

***Important:*** If you choose to use the Adjacency Matrix representation, you will recieve a ***maximum*** 5 on Program Speed and 5 on Style, Comments, & Implementation. Hence, using the Adjacency Matrix Representation will yield a ***max total 75 points.***

#### Program Correctness

As mentioned, you must ensure your program outputs match the reference TA executables'. This includes error checking. Your program will also be run on a larger graph not provided.

#### Program Speed

In this assignment, your program must also be efficient. Your program speed score will be determined by the fastest running program from your classmates (i.e. the fastest running program will recieve full credit, and rest will be scored compared to it).
Note: If your implementation is slower than the reference, you will recieve no points for program speed. The reference executable is a very basic Dijkstra's implementation seen from lecture, and designed to be inefficient!

***Note:*** If your program does not pass the correctness tests, you will not recieve points for program speed!

To summarize, if your program is correct and within 10% of the TA reference, you can recieve a ***max total 90 points*** (assuming full credit in implementation and corectness). The remaining 10 points will be awarded proportional to how much faster your program is.

If you are able to outperform the TA implementation by using a more optimized Dijkstra's Algorithm approach, you will recieve an additional ***5 points extra credit***. (Hint: the efficient algorithm should use priority queue/heap).

#### Style, Comments, & Implementation
Your code needs to be commented and styled.
It is recommended to follow the [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html). As well as being readable, you will be graded on your implementation. You should follow the [C++ Coding Standards and Best Practices](https://web.mit.edu/6.s096/www/standards.html). You must ensure you are using the correct OOP practices and data structures.

#### Interactive Grading

Since this is a group assignment, there will be interactive grading for this project. This is just to verify that all members understand the code fully. Hence, this will be individual -- to make sure you succeed, make sure you understand all of your submitted code, even if there are parts you did not code yourself.

## Submission

Push all your code (all includes, src files, Makefile) to your Github Repository before the deadline. There is no late deadline for this assignment to accomodate interactive grading.

## Credits
Kartik Patwari, Jeff Lai, Chen-Nee Chuah
