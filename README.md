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
---------------

Usage
-----

### Importing the package

Import the necessary packages from the EBSL-Go project:

goCopy code

`import ( 	"github.com/yourusername/ebsl-go/evidence" 	"github.com/yourusername/ebsl-go/opinion" 	"github.com/yourusername/ebsl-go/trust" 	"github.com/yourusername/ebsl-go/trust/equations" 	"github.com/yourusername/ebsl-go/trust/equations/solver" )`

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


Mathematical Model
------------------

The EBSL mathematical model is based on the idea of an opinion, which is a subjective evaluation of the probability of an event. An opinion is represented by a triplet (belief, disbelief, and uncertainty), where belief is the degree of belief that the event will occur, disbelief is the degree of belief that the event will not occur, and uncertainty is the degree of ignorance about the event. The belief, disbelief, and uncertainty values must sum to 1.

EBSL also includes the concept of a trust, which is a measure of the degree to which one agent trusts another agent. Trust is represented as an opinion about the trustworthiness of the other agent.

The EBSL model provides a way to combine evidence and opinions to update one's beliefs about an event. This is done using the Bayesian update rule, which combines the prior belief with the new evidence to form a posterior belief. EBSL extends this idea to incorporate subjective opinions and uncertainty, allowing for more nuanced reasoning.


