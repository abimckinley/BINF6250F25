# Introduction
In this project we created functions that generate Markov models based on input text, from 1st order to Nth order, from single-line text to complex scripts. Markov chains are sequences of events in which the probablility of the next event depends only on the present state. In this project, our "states" were words in sentences, or sentences in a full file of text. To complete this task, we built dictionaries that use "current status" as keys, and dictionaries of the frequency pairs of "next status" as values. Based on that, we implemented functions that calculate probabilities and come up with predicted "next status" from a Markov model.

# Pseudocode
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

# Train with Shakespeare Sonnets
sonnet_markov_model = empty dictionary
FOR each block of text in sonnets file (separated by blank line):
    sonnet_markov_model = build_markov_model(sonnet_markov_model, block_text, order=2)

PRINT generate_random_text(sonnet_markov_model, seed=7)
 
```

# Successes
We had a very productive first discussion where we mapped out the steps for each function and implemented their pseudocode. This allowed us to quickly complete the Python code later. We realized that clarifying the relationships between the functions' tasks before we started the actual programming was the key to our success. 

# Struggles
We ran into a few programming errors while applying some specific Python functions, but we were able to find and fix them by carefully reviewing the code and looking up the functions' usage.

In the final function, 'Shakespeare,' we were initially confused about the purpose of the 'sonet' variable and the difference between this function and the 'all the fish' function. However, after reviewing the original text used to train the model, we realized that 'Shakespeare' trains a separate model for each paragraph separated by a blank line.

# Personal Reflections
## Group Leader - Abi
We wound up running into only a couple of issues, which were resolved fairly easily. Writing the pseudocode first, and almost exactly how we would write our code made the process of completing each function much smoother. We communicated well about our individual progress, and our respective knowledge in certain areas made the process of writing the code fairly seamless. If there was something that I missed when writing a specific function, Tiange was able to help me see what I was missing, and of the functions that we both worked on, our ideas were very similar!

## Other member - Tiange
The assignment went very smoothly because Abi and I prepared our ideas before each meeting, which allowed us to make quick progress. During this process, I reviewed my knowledge of Python dictionaries. The experience of debugging the issues we ran into was especially helpful, as it made me aware of the gaps in my initial thinking.

# Generative AI Appendix
Gemini was used to help with debugging.
