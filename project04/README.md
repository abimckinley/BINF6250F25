# Introduction
In this project, we filled out a de Bruijn graph class that reads a given string, breaks it up into nodes and edges, and 
resequences the string in the appropriate order by traversing the de Bruijn graph through an Eulerian walk. 

# Pseudocode

```
FUNCTION add_edge(left, right)
''' This function adds a new edge to the graph
        Args:
            left (str): The k-1 mer for the left edge
            right (str): The k-1 mer for the right edge

        Updates graph attribute to add right to the list named left in defaultdict   
'''
If left not in graph:
    initialize graph[left] as empty list
Append right to graph[left]
If first_node is empty:
    set first_node = left
```
```
FUNCTION remove_edge(left, right)
''' This function removes an edge from the graph
        Args:
            left (str): The k-1 mer for the left edge
            right (str): The k-1 mer for the right edge

        Updates graph attribute to remove right from the list named left in defaultdict
'''
If left in graph:
    If right in graph[left]:
        remove right from graph[left]
```
```
FUNCTION dfs(left, visited):
        Mark left as visited
        For each neighbor right of left:
            If right is not visited:
                Call dfs(right, visited)
```
```
FUNCTION is_connected():
        Create dictionary visited with all nodes set to False
        Find a node with at least one outgoing edge and set as start
        If no such node exists:
            Return True
        Call dfs(start, visited)
        For each node in graph:
            If node has edges and is not visited:
                Return False
        Return True
```
```
FUNCTION eulerian_walk():
        If graph is not connected:
            Return False
        Initialize in_degree and out_degree for all nodes
        For each node left:
            Increase out_degree[left] by number of outgoing edges
            For each neighbor right of left:
                Increase in_degree[right]
        Initialize start_nodes = 0, end_nodes = 0
        For each node in set of all nodes:
            If out_degree[node] - in_degree[node] == 1:
                Increase start_nodes
            Else if in_degree[node] - out_degree[node] == 1:
                Increase end_nodes
            Else if in_degree[node] != out_degree[node]:
                Return True
```
```
FUNCTION build_debruijn_graph(input_string, k)
''' This function builds a De Buijn graph from a string
        Args:
            input_string (str): string to use for building the graph
            k (int): k-mer length for graph construction

        Updates graph attribute to add all valid edges from the string
        
        Example:
        >>> dbg = DeBruijnGraph("this this this is a test", 4)
        >>> print(dbg.graph) #doctest: +ELLIPSIS +NORMALIZE_WHITESPACE
        defaultdict(<class 'list'>, {'thi': ['his', 'his', 'his'], 'his': ['is ', 'is ', 'is '], ...)
'''
```
```
FUNCTION print_eulerian_walk():
''' This function starts the recursive walk function
        at the first node in the graph
        
        Args: None
        
        Returns:
            tour (list): list of k-1 mers traversed by the algorithm
        
        Example:
        >>> dbg = DeBruijnGraph("this this this is a test", 4)
        >>> dbg.print_eulerian_walk(seed=1) #doctest: +ELLIPSIS +NORMALIZE_WHITESPACE
        ['thi', ...]
        '''
        Initialize tour as empty list
        Choose start as any node in graph
        Call print_eulerian_walk(start, tour)
        Reverse tour
        Return tour
```
```
FUNCTION eulerian_helper(left, tour):
        While left has outgoing edges:
            right = first neighbor of left
            Call remove_edge(left, right)
            Call print_euerlian_walk(right, tour)
        Append left to tour
```

# Successes
We were able to learn more about both recusrion and graph theory, and were able to successfully produce the desired results, which we are pleased with. The two of us have worked together before, so we were able to communicate effectively, and made time to meet and go through pseodocode and actual code. We talked through everything, and were able to help one another with certain sticking points. 

# Struggles
We were having some trouble at first getting the full sentence as the result in the correct order because we were starting with a random node rather than writing the program to automatically start at the first node. We also had a bit of trouble understanding how to code the recursion, but after doing some further research, we were able to get a better grasp on the process. 

# Personal Reflections
## Group Leader - Abi
I thought this project was fun and enjoyable, but slightly difficult as well. I know a fair amount about graph theory and have worked with systems of nodes and their relationships quite a bit in my undergrad, but did not have to do extensive programming along with that work. Therefore, I understood the underlying theories and algorithms in place for this assignment, but spent most of my time trying to figure out how to code for them. I do not have much experience with recursion, so it was nice to get some more practice using it in a way that I was (mostly) able to understand what was going on. 

## Other member - Jason
I thought this project was quite enlightening to a process I did not know the mechanics behind: de novo sequencing. Graph theory is a new concept to me that I struggled to visualize initially, but once I understood it it became a fun puzzle. It is cool to see the basics behind how researchers can be confident that the sequence they get is correct without a known reference. I am also happy to be able to apply recursion, it's a rare treat.

# Generative AI Appendix
We did not use AI, but we did use a few outside sources to aid in our completion of this project. I am attaching links so that they are hopefully interesting and useful to you all as well!
https://pmc.ncbi.nlm.nih.gov/articles/PMC5531759/
https://www.geeksforgeeks.org/dsa/eulerian-path-eulerian-circuit-in-python/
