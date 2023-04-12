EBSL-Go
=======

EBSL-Go is a Go library that implements the Evidence Based Subjective Logic (EBSL) mathematical model. EBSL is a probabilistic logic model that allows for reasoning with uncertain and subjective evidence. It is a useful tool for making decisions in situations where there is incomplete or uncertain information.

Overview
--------

The EBSL-Go library consists of several packages and files:

*   `evidence/evidence.go`: This package contains types and functions for representing and working with evidence.
*   `opinion/opinion.go`: This package contains types and functions for representing and working with opinions.
*   `trust/trust.go`: This package contains types and functions for representing and working with trust.
*   `trust/equations/equations.go`: This package contains types and functions for defining and solving trust equations.
*   `trust/equations/expressionevaluator.go`: This package contains an expression evaluator used by the trust equation solver.
*   `trust/equations/solver/solver.go`: This package contains a solver for trust equations.

Mathematical Model
------------------

The EBSL mathematical model is based on the idea of an opinion, which is a subjective evaluation of the probability of an event. An opinion is represented by a triplet (belief, disbelief, and uncertainty), where belief is the degree of belief that the event will occur, disbelief is the degree of belief that the event will not occur, and uncertainty is the degree of ignorance about the event. The belief, disbelief, and uncertainty values must sum to 1.

EBSL also includes the concept of a trust, which is a measure of the degree to which one agent trusts another agent. Trust is represented as an opinion about the trustworthiness of the other agent.

The EBSL model provides a way to combine evidence and opinions to update one's beliefs about an event. This is done using the Bayesian update rule, which combines the prior belief with the new evidence to form a posterior belief. EBSL extends this idea to incorporate subjective opinions and uncertainty, allowing for more nuanced reasoning.

Implementation
--------------

The EBSL-Go library provides a Go implementation of the EBSL mathematical model. The `evidence` package provides types and functions for representing and working with evidence, such as `Evidence` and `EvidenceSet`. The `opinion` package provides types and functions for representing and working with opinions, such as `Opinion` and `OpinionSet`. The `trust` package provides types and functions for representing and working with trust, such as `Trust` and `TrustSet`.

The `trust/equations` package provides types and functions for defining and solving trust equations. Trust equations are used to update trust opinions based on evidence and other trust opinions. The `ExpressionEvaluator` type in `expressionevaluator.go` is used to evaluate expressions in trust equations, and the `Solver` type in `solver.go` is used to solve the equations.
