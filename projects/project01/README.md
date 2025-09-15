# Introduction
The aim of this project was to utilize strings to extract certain pieces of information from a file. More specifically, the program parses the program to identify rare variants of a variety of diseases based on their "AF_EXAC" value. As outlined in the pseodocode below, our program parses the VSF file line by line to identify rare variants. Associated diseases are pulled from the CDLN column, and put into their own list. The end result is a returned summary of each disease obvserved to have a rare variant. 

# Pseudocode
```
FUNCTION parse_line(line):
    IF "AF_EXAC" not in line:
        RETURN empty list
    
    Extract AF_EXAC value from line
    Convert AF_EXAC value to number
    
    IF AF_EXAC < 0.0001:
        Extract CLNDN (disease names) from line
        Split CLNDN into a list (diseases may be separated by commas or '|')
        
        Initialize empty list: valid_diseases
        FOR each disease in extracted list:
            IF disease is NOT "not_specified" AND NOT "not_provided":
                Add disease to valid_diseases
        RETURN valid_diseases
    ELSE:
        RETURN empty list
END FUNCTION


FUNCTION read_file(filename):
    Open file with name = filename
    
    Initialize empty dictionary: disease_counts
    
    FOR each line in file:
        IF line starts with "#" (header line in VCF):
            CONTINUE to next line
        
        diseases = parse_line(line)
        
        FOR each disease in diseases:
            IF disease in disease_counts:
                disease_counts[disease] = disease_counts[disease] + 1
            ELSE:
                disease_counts[disease] = 1
    
    Close file
    RETURN disease_counts
END FUNCTION


MAIN PROGRAM:
    results = read_file("clinvar_20190923_short.vcf")
    PRINT results
```

# Successes
We feel as though this project went well, which was aided by going through the instructions line by line when writing the pseodocude. The program followed our pseodocode pretty accurately, which allowed us to get through the code smoothly and efficiently. We tried to make the code as clear and intentional as possible while also producing accurate results and ensuring that we hit all requirements in the instructions. We stayed in communication as much as possible about our respective progress on the project, which made completing it much easier. 

# Struggles
Our main sticking point was making the code as concise as possible, which meant trying to cut down on the amount of "if" statements we were utilizing, and using "elif" instead. We took our time when editing the code to ensure that all requirements were taken care of, and written in such a way that they followed the instructions. Another issue we were having was getting the filters to properly filter the column names that we wanted, which was an issue at the beginnning. Another element we took our time on was determining which funcition we were going to write first. At first, it made sense to us to write the functions in the order they would run, but in the end it made the most sense to write the functions backwards, since we knew what the end result was that we were trying to produce.

# Personal Reflections
## Abi
This project was a good refresher for me, to get back into a coding mindset. I think that it utilized some important things that we learned in previous courses, and I found myself going back to some notes before diving into the project fully. Writing the pseodocode first was incredibly helpful, and made it much easier to understand the project. 

## Jason
I thought this was a fun and appropriately challenging first project to tackle. I feel like there were way more pretty ways to filter for all of the conditions than the countless "if" statements, but I am personally too novice to think of them or know how to use them.

# Generative AI Appendix
As per the syllabus
