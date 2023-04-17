EBSL-Go
=======

EBSL-Go is an implementation of Evidence-Based Subjective Logic (EBSL) in Go. It provides a framework for modeling and analyzing trust relationships between entities in a network using a mathematical approach based on evidence and opinions.

Features
--------

*   Representation of direct and final referral trust relationships.
*   Conversion of evidence-based trust relationships to subjective opinions.
*   Calculation of final referral trust values using iterative solvers.
*   Customizable solver options, distance functions, and aggregators.
*   Interfaces for trust matrix iteration and manipulation.

Getting Started 
-----

### Importing the package

Import the necessary packages from the EBSL-Go project:

`import ( 	"github.com/BraveNewCapital/ebsl-go/evidence" 	"github.com/BraveNewCapital/ebsl-go/opinion" 	"github.com/BraveNewCapital/ebsl-go/trust" 	"github.com/BraveNewCapital/ebsl-go/trust/equations" 	"github.com/BraveNewCapital/ebsl-go/trust/equations/solver" )`

### Direct and Final Referral Trust

1.  Create direct referral trust relationships as a map of links and evidence:


`directReferralEvidence := trust.DirectReferralEvidence{ 	trust.Link{From: 1, To: 2}: evidence.Type{P: 4, N: 1}, 	trust.Link{From: 2, To: 3}: evidence.Type{P: 2, N: 2}, 	// ... more relationships ... }`

2.  Convert direct referral trust relationships to opinion space:


`c := uint64(2) // Discount factor directReferralOpinion := directReferralEvidence.ToDirectReferralOpinion(c)`

3.  Define a final referral trust equation context and set of equations:


`context := equations.NewFinalReferralTrustEquationContext(directReferralOpinion) eqs := equations.NewFinalReferralTrustEquations(directReferralOpinion)`

4.  Solve the final referral trust equations using the solver:


`err := solver.SolveFinalReferralTrustEquations(context, eqs) if err != nil { 	panic(err) }`

5.  Access the final referral trust values:


`finalReferralTrust := context.GetFinalReferralTrust(trust.Link{From: 1, To: 3}) fmt.Printf("Final referral trust: %+v\n", finalReferralTrust)`

Customizing the Solver
----------------------

You can customize the solver by passing options to the `SolveFinalReferralTrustEquations` function:


`err := solver.SolveFinalReferralTrustEquations( 	context, eqs, 	solver.UseMaxEpochs(200), 	solver.UseEuclideanDistance(), 	solver.UseSumDistanceAggregator(), 	solver.UseTolerance(0.001), 	solver.UseOnEpochStartCallback(func(epoch uint) error { 		fmt.Printf("Epoch %d started\n", epoch) 		return nil 	}), 	solver.UseOnEpochEndCallback(func(epoch uint, aggregatedDistance float64) error { 		fmt.Printf("Epoch %d ended, aggregated distance: %f\n", epoch, aggregatedDistance) 		return nil 	}), )`

----------------------

## Project overview

Description of each file and how they work together as part of the EBSL-Go Project:

1.  `evidence.go`:

The `evidence.go` file is part of the `evidence` package. This file provides the basic types and functions for handling evidence data in EBSL-Go. It defines the `Type` struct for evidence, containing belief (b), disbelief (d), and uncertainty (u) values, and several utility functions for working with evidence, such as adding and normalizing evidence.

In the context of the EBSL-Go project, this file is responsible for providing the foundation for representing evidence and operations on evidence data.

2.  `opinion.go`:

The `opinion.go` file is part of the `opinion` package. This file provides the basic types and functions for handling opinions in EBSL-Go. It defines the `Type` struct for opinions, containing belief (B), disbelief (D), and uncertainty (U) values, and several utility functions for working with opinions, such as converting evidence to opinion using a given discount factor (c), calculating expected belief, and performing fusion operations on opinions.

In the context of the EBSL-Go project, this file is responsible for representing opinions and operations on opinions. Opinions are used to represent trust values in the trust network.

3.  `trust/equations/equations.go`:

The `equations.go` file is part of the `trust/equations` package. This file provides types and interfaces for defining and working with final referral trust equations in EBSL-Go. The main types and interfaces in this file are `FinalReferralTrustEquation`, `IterableFinalReferralTrustEquations`, `FinalReferralTrustEquationContext`, and `FinalReferralTrustEquationIterator`.

In the context of the EBSL-Go project, this file is responsible for providing the structure for final referral trust equations, which are used to calculate final referral trust values in a trust network.

4.  `trust/equations/solver/solver.go`:

The `solver.go` file is part of the `trust/equations/solver` package. This file provides a solver for the final referral trust equations. It provides the `SolveFinalReferralTrustEquations` function, which takes a context, an iterable set of final referral trust equations, and solver options, and iteratively solves the equations to find final referral trust values in the trust network.

In the context of the EBSL-Go project, this file is responsible for solving the final referral trust equations, allowing the calculation of final referral trust values in the trust network.

5.  `trust/trust.go`:

The `trust.go` file is part of the `trust` package. This file provides structures and types for representing trust networks, including trust direction (links), direct referral trust in both evidence and opinion space, and final referral trust. It defines types such as `Link`, `DirectReferralEvidence`, `DirectReferralOpinion`, `DirectFunctionalTrust`, and `FinalReferralOpinion`.

In the context of the EBSL-Go project, this file is responsible for providing the structure and types for representing trust networks and various trust matrices. It works with the other files to create, represent, and manipulate trust networks in the EBSL-Go system.

Overall, these files work together to create a holistic EBSL-Go project that represents and manipulates trust networks. The project starts with basic types for evidence and opinions, builds upon them to represent trust networks and final referral trust equations, and provides solvers to calculate final referral trust values in the trust network.


Mathematical Model
------------------

The EBSL mathematical model is based on the idea of an opinion, which is a subjective evaluation of the probability of an event. An opinion is represented by a triplet (belief, disbelief, and uncertainty), where belief is the degree of belief that the event will occur, disbelief is the degree of belief that the event will not occur, and uncertainty is the degree of ignorance about the event. The belief, disbelief, and uncertainty values must sum to 1.

EBSL also includes the concept of a trust, which is a measure of the degree to which one agent trusts another agent. Trust is represented as an opinion about the trustworthiness of the other agent.

The EBSL model provides a way to combine evidence and opinions to update one's beliefs about an event. This is done using the Bayesian update rule, which combines the prior belief with the new evidence to form a posterior belief. EBSL extends this idea to incorporate subjective opinions and uncertainty, allowing for more nuanced reasoning.


