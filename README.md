# Huffman-Coding

## Aim
To implement Huffman Coding to compress the data using Python.

---

# Software Required
1. Anaconda Navigator
2. Python 3.7 or above
3. Jupyter Notebook

---

# Theory
Huffman Coding is a lossless data compression algorithm used to reduce the size of data. It assigns variable-length binary codes to characters based on their frequency of occurrence. Characters with higher frequency receive shorter codes, while characters with lower frequency receive longer codes.

The Huffman tree is constructed using a greedy approach by repeatedly combining the two nodes with the smallest frequencies until a single tree is formed.

---


# Algorithm

## Step 1:
Get the input string from the user.

## Step 2:
Calculate the frequency of occurrence of each character in the string.

## Step 3:
Create Huffman tree nodes based on character frequencies.

## Step 4:
Generate Huffman codes by traversing the Huffman tree.

## Step 5:
Display the characters along with their Huffman codes.

---
## Name : SHADHANASHREE S V  
## Register Number : 212223230202  
# Program

```python
# Huffman Coding in Python

class Node:
    def __init__(self, freq, symbol, left=None, right=None):
        self.freq = freq
        self.symbol = symbol
        self.left = left
        self.right = right
        self.huff = ''

# Function to print Huffman Codes

def printNodes(node, val=''):
    newVal = val + str(node.huff)

    if(node.left):
        printNodes(node.left, newVal)

    if(node.right):
        printNodes(node.right, newVal)

    if(not node.left and not node.right):
        print(f"{node.symbol} -> {newVal}")

# Input String
string = input("Enter the string: ")

# Calculate frequency of characters
chars = {}

for char in string:
    if char in chars:
        chars[char] += 1
    else:
        chars[char] = 1

# Create Huffman Tree Nodes
nodes = []

for char, freq in chars.items():
    nodes.append(Node(freq, char))

# Build Huffman Tree
while len(nodes) > 1:

    nodes = sorted(nodes, key=lambda x: x.freq)

    left = nodes[0]
    right = nodes[1]

    left.huff = 0
    right.huff = 1

    newNode = Node(left.freq + right.freq,
                   left.symbol + right.symbol,
                   left,
                   right)

    nodes.remove(left)
    nodes.remove(right)
    nodes.append(newNode)

# Print Huffman Codes
print("\nCharacters and their Huffman Codes:")

printNodes(nodes[0])
```

---

# Sample Input

```python
Enter the string: "huffman coding"
```

---

# Output

```python
<img width="247" height="327" alt="image" src="https://github.com/user-attachments/assets/7f5c6f8c-7cf9-4962-b947-2c7b06fbfaec" />

```

---

# Result
Thus the Huffman Coding algorithm was implemented successfully using Python programming to compress the data.
