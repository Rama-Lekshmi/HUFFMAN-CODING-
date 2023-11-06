# Implementation-of-Huffman-Coding-Algorithm
## Aim:
To implement Huffman coding to compress the data using Python.

## Software Required:
1. Anaconda - Python 3.7

## Algorithm:
### Step 1: 
Assign the input string.
### Step 2:
Create the required tree nodes.
### Step 3:
Create a function to implement the huffman coding.
### Step 4:
Calculate frequency of occurence.
### Step 5:
Print the characters and its Huffman code.
## Program:
~~~
Developed by : Javith farkhan S
Registration Number : 212221240017
~~~
### Get the input String:
~~~
string=input("Enter a string")
class NodeTree(object):
  def __init__(self,left=None,right=None):
    self.left=left
    self.right=right
  def children(self):
    return(self.left,self.right)
~~~        
### Create tree nodes:
~~~
def huffman_code(Node,left=True,binstring=''):
  if type(Node) is str:
    return {Node: binstring}
  (l,r) = Node.children()
  d=dict()
  d.update(huffman_code(l,True,binstring + '0'))
  d.update(huffman_code(r,False,binstring + '1'))
  return d
~~~    
### Main function to implement huffman coding:
~~~
freq={}
for c in string:
  if c in freq:
    freq[c]+=1
  else:
    freq[c]=1
freq=sorted(freq.items(),key = lambda x: x[1],reverse=True)
Nodes=freq
~~~
### Calculate frequency of occurrence:
~~~
while len(Nodes) >1:
  (key1,c1) =Nodes[-1]
  (key2,c2) =Nodes[-2]
  Nodes=Nodes[:-2]
  Node=NodeTree(key1,key2)
  Nodes.append((Node,c1+c2))
  Nodes=sorted(Nodes,key=lambda x: x[1],reverse=True)
~~~    
### Print the characters and its huffmancode:
~~~

huffmancode=huffman_code(Nodes[0][0])
print('Char | Code')
for (char,frequency) in freq:
  print('%-4r |%12s' % (char, huffmancode[char]))
~~~
## Output:

![DIP_12 1](https://github.com/Javith-farkhan/Huffman-Coding/assets/94296805/55a531d4-def4-467e-a087-2114bd7f6960)



## Result:

Thus, the huffman coding was implemented to compress the data using python programming.
