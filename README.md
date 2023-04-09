EBSL-Go
=======

EBSL-Go is a Go implementation of Evidence Based Subjective Logic (EBSL). EBSL is an extension of Subjective Logic, which is a mathematical framework for reasoning under uncertainty and opinions. EBSL incorporates evidences into subjective logic to enable evidence-based reasoning.

This project consists of four main files:

*   `evidence.go`: provides the definition of the evidence and its operations.
*   `opinion.go`: provides the definition of the opinion and its operations.
*   `trust.go`: provides the definition of the trust and its operations.
*   `util.go`: provides utility functions.

Usage
-----

To use this project, you can import the relevant files into your Go project and use the provided structs and functions. For example:

goCopy code


``` // Create an opinion with a belief of 0.3, disbelief of 0.2, and uncertainty of 0.5
op := opinion.Opinion{Belief: 0.3, Disbelief: 0.2, Uncertainty: 0.5}  

// Combine two opinions using Dempster's rule of combination 
combinedOp := opinion.Combine(op1, op2)
```


Refer to the individual files for more information on the available functions and structs.
