Overview
--------

`evidence.go` is a Go file in the EBSL-Go project that defines the evidence types used in the Evidence Based Subjective Logic (EBSL) framework. The file contains several types and methods that are used to create and manipulate different types of evidence.

The evidence types defined in this file are used to represent the degree of trust that an agent has in another agent or the accuracy of a piece of information. The different types of evidence that can be represented include direct evidence, indirect evidence, and consensus evidence.

Types
-----

The following types are defined in `evidence.go`:

*   `Type`: This is an interface that defines the methods that all evidence types must implement.
*   `Direct`: This is a struct that represents direct evidence.
*   `Indirect`: This is a struct that represents indirect evidence.
*   `Consensus`: This is a struct that represents consensus evidence.

Methods
-------

The following methods are defined in `evidence.go`:

*   `FromDirect(direct Direct) Type`: This method returns a `Type` interface that represents direct evidence.
*   `FromIndirect(indirect Indirect) Type`: This method returns a `Type` interface that represents indirect evidence.
*   `FromConsensus(consensus Consensus) Type`: This method returns a `Type` interface that represents consensus evidence.
*   `Value() float64`: This method returns the value of the evidence type as a float64.

Example Usage
-------------

goCopy code

```
package main 

import ( 	"fmt"  	"evidence" )  

func main() { 
// Create some evidence types 
direct := evidence.Direct{Value: 0.8} 
indirect := evidence.Indirect{Value: 0.6} 
consensus := evidence.Consensus{Positive: 3, Negative: 1} 

// Convert them to the Type interface 
evidence1 := evidence.FromDirect(direct) 	
evidence2 := evidence.FromIndirect(indirect) 	
evidence3 := evidence.FromConsensus(consensus)  	

// Print their values 	
fmt.Println(evidence1.Value()) // Output: 0.8
fmt.Println(evidence2.Value()) // Output: 0.6
fmt.Println(evidence3.Value()) // Output: 0.75 }
```

In the example above, we create three different types of evidence.
 -direct
 -indirect
 -consensus
We convert them to the `Type` interface using the `FromDirect()`, `FromIndirect()`, and `FromConsensus()` methods.
We then print out the value of each evidence type using the `Value()` method.
