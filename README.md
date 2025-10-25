# BINF6250F25
# Introduction
Description of the project

# Pseudocode
##Section on BWT
```
```

## Section on BWT from suffix arrays 
```
function suffix_array(text)
1.   Create a list of all suffixes of the text, each paired with its starting position 
      a. (tuples) (start_pos suffix) (list of len+1 of (start_pos suffix))
      b. start with (0 string$) ; then (1 tring$); then (2 ring$); then 
      (3 ing); then (4 ng$) then (5 g$) then (6 $)
2.  Sort these suffix-position pairs lexicographially by suffix into a new list/array
3.  Extract just the starting positions from the sorted pairs; ident original position
4.  return(list of sorted starting positions)

function BWT_from_suffix_array (text, suffix_positions (list of int?))
1. Initialize on empty string of the same length as input text.
2. for each position in the suffix positions list do
3.    if the suffix starts that the beginning of the text then
4.      Add the last character of the text to the transformed result
5.    else
6.      Add the character preceeding the suffix to the transformed result
7. Return(the transformed result)

Example:  BWT_from_suffix_array("banana$", [6, 5, 3, 1, 0, 4, 2])
  transformed = string 7 char long
  for i = 0 to 6 do
    if text[0] == '$'
      add last character of the text to the transformed result.
    else
      add the character preceeding the suffix to the transformed result
      transformed[i] = character sorted suffix array paired with original lookup
          Ex transformed[0] = 'a'
             transformed[1] = 'n'
             transformed[2] = 'n'
             transformed[3] = 'b'
             transformed[4] = '$' # Note that this is 0 -- I put in [6]
             transformed[5] = 'a'
             transformed[6] = 'a'
             (answer should be:  'annb$aa' (check!))
  return(transformed)
```
## FM-Index for Pattern Matching
```
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
