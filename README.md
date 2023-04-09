# EBSL-Go
---

#### EBSL-Go is a Go implementation of Evidence Based Subjective Logic (EBSL). EBSL is an extension of Subjective Logic, which is a mathematical framework for reasoning under uncertainty and opinions. EBSL incorporates evidences into subjective logic to enable evidence-based reasoning.

This project consists of the implementation files:

*   `evidence.go`: provides the definition of the evidence and its operations.
*   `opinion.go`: provides the definition of the opinion and its operations.
*   `trust.go`: provides the definition of the trust and its operations.
*   `util.go`: provides utility functions.
*   `equations.go`: Defines the basic equations used to combine evidence and compute opinions in the EBSL system. It includes functions to compute belief, disbelief, and uncertainty from evidence, as well as functions to combine opinions using the Cumulative Belief Function (CBF) and the Cumulative Disbelief Function (CDF).
*   `solver.go`: Defines the Solver type, which is used to compute the belief, disbelief, and uncertainty of a set of hypotheses given a set of evidence. It includes functions to initialize and update the solver, as well as to compute the opinions of the hypotheses.

Usage
-----

To use this project, you can import the relevant files into your Go project and use the provided structs and functions. For example:


``` // Create an opinion with a belief of 0.3, disbelief of 0.2, and uncertainty of 0.5
op := opinion.Opinion{Belief: 0.3, Disbelief: 0.2, Uncertainty: 0.5}  

// Combine two opinions using Dempster's rule of combination 
combinedOp := opinion.Combine(op1, op2)
```

The EBSL system is composed of several files that work together to enable modeling, analysis, and manipulation of subjective beliefs and trust relationships. 

Together, these files enable the EBSL system to model and reason about subjective beliefs and trust relationships, which can be used in a variety of applications, such as decentralized identity with social graphs, reputation systems, and sybil control for crypto airdrops.
How the Files Work Together

  - evidence.go Used by other files to represent and reason about different types of evidence, such as direct referral trust evidence in the trust.go file.

  - equations.go Defines the basic equations used to compute opinions from evidence, such as the CBF and the CDF. This file is used by the solver.go file to compute the opinions of a set of hypotheses given a set of evidence.

  - solver.go Defines the Solver type, which is used to compute the opinions of a set of hypotheses given a set of evidence. This file uses the equations.go file to compute the opinions and updates the beliefs of the hypotheses based on new evidence.

  - trust.go Defines the Link and DirectReferralEvidence types, which are used to represent trust relationships between entities. This file also defines functions to transform direct referral trust evidence into opinion space and to compute the final referral trust opinion of a set of entities. These functions use the solver.go file to compute the opinions of the entities and combine them to generate the final referral trust opinion.

  - utils.go Defines utility functions used by other files, such as functions to compute the power set of a set and to generate random numbers. These functions are used by other files to generate and manipulate sets of data.

In summary, the evidence.go and equations.go files provide the basic building blocks to represent and reason about different types of evidence and opinions, while the solver.go file provides a higher-level interface to compute opinions and update beliefs based on new evidence. The trust.go file extends the EBSL system to model trust
