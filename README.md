# Exp - 11  Implementation-of-the-Huffman-Coding-algorithm
# Name : JISHNUPRIYAN S
# Reg. no : 212223240061 


# Aim :
To implement the Huffman Coding algorithm for the given input string and generate a unique binary code for each character based on its frequency.

# Algorithm :

### Step : 1

Get the input string and count the frequency of each character.


### Step : 2

Create nodes for each character along with its frequency.


### Step : 3

Select the two nodes with the lowest frequencies and combine them into a new node.


### Step : 4

Repeat the process until only one node remains to form the Huffman tree.


### Step : 5

Generate Huffman codes by assigning 0 to the left branch and 1 to the right branch, then display the codes.


# Program :

```py

# Step 1: Get the input string
input_string = "JISHNUPRIYAN S"  # Example input string

# Step 2: Calculate frequency of each character in the input string
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]


# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)


# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")



```



# Output :

<img width="327" height="285" alt="Screenshot 2026-09-07 083547" src="https://github.com/user-attachments/assets/e975eb9f-4c49-4471-aa00-2ba91c0bed9f" />






# Result :
 The Huffman Coding algorithm was successfully implemented, and Huffman codes were generated for the characters in “JISHNUPRIYAN S”.
