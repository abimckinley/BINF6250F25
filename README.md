# BINF6250F25
# Introduction
Description of the project

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
