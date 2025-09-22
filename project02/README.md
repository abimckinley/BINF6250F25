# Introduction
Description of the project

# Pseudocode
Put pseudocode in this box:

```
FUNCTION build_markov_model(markov_model, new_text):
    ADD special start token "*S*" at beginning of new_text
    ADD special end token "*E*" at end of new_text
    
    SPLIT new_text into words
    
    FOR i from 0 to length(words) - 2:
        current_word = words[i]
        next_word = words[i+1]
        
        IF current_word not in markov_model:
            markov_model[current_word] = empty dictionary
        
        IF next_word not in markov_model[current_word]:
            markov_model[current_word][next_word] = 0
        
        INCREMENT markov_model[current_word][next_word] by 1
    
    RETURN markov_model

FUNCTION build_markov_model(markov_model, text, order):
    ADD special start token "*S*" repeated 'order' times
    ADD special end token "*E*"
    
    SPLIT text into words
    CREATE padded_words = [*S* repeated 'order' times] + words + [*E*]
    
    FOR i from 0 to length(padded_words) - order - 1:
        state = tuple(padded_words[i : i+order])   # Current N-word state
        next_word = padded_words[i + order]
        
        IF state not in markov_model:
            markov_model[state] = empty dictionary
        
        IF next_word not in markov_model[state]:
            markov_model[state][next_word] = 0
        
        INCREMENT markov_model[state][next_word] by 1
    
    RETURN markov_model

FUNCTION get_next_word(current_state, markov_model, seed):
    next_words = keys of markov_model[current_state]
    frequencies = values of markov_model[current_state]
    total = SUM of frequencies
    
    probabilities = [frequency / total for each frequency]
    
    USE random generator (seeded if given) to choose one word
    RETURN chosen next_word

import random 
FUNCTION generate_random_text(markov_model, seed=42):
# Set the seed for reproducibility 
random.seed(seed) 
# Get all keys as a list 
keys_list = list(dictionary.keys()) 
# Randomly choose one key from the list 
random_key = random.choice(keys_list) 
return random_key

FUNCTION train_model_from_file(filename, order):
    OPEN file
    READ text into string
    CLOSE file
    
    markov_model = empty dictionary
    markov_model = build_markov_model(markov_model, text, order)
    
    RETURN markov_model

# New function to turn text files into strings
 
FUNCTION train_from_file(filename, order):
    OPEN file
    READ text into string
    CLOSE file
    
    markov_model = empty dictionary
    markov_model = build_markov_model(markov_model, text, order)
    
    RETURN markov_model

# Train with Dr. Seuss book
markov_model = train_from_file("data/one_fish_two_fish.txt", order=2)
PRINT generate_random_text(markov_model, seed=7)

# ADD SHAKESPEARE
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
