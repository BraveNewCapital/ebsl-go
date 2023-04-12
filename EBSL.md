# EBSL
### Evidence-Based Subjective Logic

---

Evidence-Based Subjective Logic (EBSL) is a mathematical model used for reasoning under uncertainty. It extends classical Bayesian probability theory to incorporate subjective opinions, and combines both evidence and trust in a unified framework. EBSL is used to calculate the probability of events or hypotheses that are uncertain, based on subjective opinions from multiple sources.

The EBSL model consists of several components, including:

1.  Belief (B) - the degree of belief in a hypothesis or event based on available evidence. This is equivalent to the likelihood in Bayesian probability theory.
    
2.  Uncertainty (U) - the degree of uncertainty in the belief. This is equivalent to the prior in Bayesian probability theory.
    
3.  Disbelief (D) - the degree of disbelief in a hypothesis or event based on available evidence.
    
4.  Base Rate (a) - the prior probability of the hypothesis or event being true, before any evidence is considered.
    
5.  Weight of Evidence (w) - the strength of the evidence supporting or opposing the hypothesis or event.
    
6.  Trust (T) - the degree of trust in the source providing the evidence.
    

In the EBSL-Go library, the EBSL model is implemented through a set of data structures and functions that allow users to create and manipulate opinions, beliefs, and trust values.

The library provides functions for creating and combining opinions from multiple sources, as well as functions for computing the belief, uncertainty, and disbelief in a hypothesis or event given a set of opinions. The library also provides functions for calculating the base rate and weight of evidence based on the available data.

For example, to create a Direct Referral Opinion (DRO) matrix in EBSL-Go, we can use the `CreateDROMatrix` function from the `trust` package. This function takes a graph represented as a map of node IDs to lists of neighbor IDs, and returns a matrix of opinions representing the direct referrals between nodes in the graph.

cssCopy code

`graph := map[int][]int{     0: {1, 2, 3},     1: {0, 2},     2: {0, 1, 3},     3: {0, 2}, }  dro := trust.CreateDROMatrix(graph)`

The `CreateDROMatrix` function calculates the trust values between nodes based on the number of shared neighbors they have, and returns a matrix of opinions representing these values.

We can also use the `CombineOpinions` function to combine opinions from multiple sources. For example, let's say we have two opinions `o1` and `o2` representing the belief and uncertainty in a hypothesis from two different sources. We can combine these opinions using the `CombineOpinions` function as follows:

cssCopy code

`o1 := evidence.NewOpinion(0.6, 0.2, 0.2) o2 := evidence.NewOpinion(0.4, 0.4, 0.2)  combined := evidence.CombineOpinions(o1, o2)`

The `CombineOpinions` function calculates the belief, uncertainty, and disbelief in the hypothesis based on the opinions from each source, and returns a new opinion representing the combined values.

Overall, the EBSL-Go library provides a powerful and flexible set of tools for reasoning under uncertainty and incorporating subjective opinions into probabilistic models.
