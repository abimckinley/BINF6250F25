# Introduction
Description of the project

# Pseudocode
Put pseudocode in this box:

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
FUNCTION print_eulerian_walk()
```
```
FUNCTION eulerian_walk()
```

# Successes
Description of the team's learning points

# Struggles
Description of the stumbling blocks the team experienced

# Personal Reflections
## Group Leader
Group leader's reflection on the project

## Other member
Other members' reflections on the project

# Generative AI Appendix
As per the syllabus
