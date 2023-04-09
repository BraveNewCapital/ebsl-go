opinion.go
----------

This file contains the implementation of the Opinion type and its related functions.

### Types

#### Opinion

`type Opinion struct { Belief float64 Disbelief float64 Uncertainty float64 BaseRate float64 }`

The `Opinion` type represents an opinion about a proposition in the evidence space. It contains four fields:

*   `Belief`: a float64 representing the degree of belief in the proposition.
*   `Disbelief`: a float64 representing the degree of disbelief in the proposition.
*   `Uncertainty`: a float64 representing the degree of uncertainty in the proposition.
*   `BaseRate`: a float64 representing the prior probability of the proposition.

### Functions

#### FromEvidence

`func FromEvidence(c uint64, ev evidence.Type) Opinion`

`FromEvidence` is a function that takes two arguments: `c` is the number of observed cases and `ev` is the type of evidence. It returns an `Opinion` struct representing the opinion about the proposition based on the given evidence.

#### ToBelief

`func (op Opinion) ToBelief() float64`

`ToBelief` is a method that returns the degree of belief in the proposition as a float64.

#### ToDisbelief

`func (op Opinion) ToDisbelief() float64`

`ToDisbelief` is a method that returns the degree of disbelief in the proposition as a float64.

#### ToUncertainty

`func (op Opinion) ToUncertainty() float64`

`ToUncertainty` is a method that returns the degree of uncertainty in the proposition as a float64.

#### ToBaseRate

`func (op Opinion) ToBaseRate() float64`

`ToBaseRate` is a method that returns the prior probability of the proposition as a float64.
