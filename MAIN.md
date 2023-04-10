Package `main`
--------------

### `func main()`

This is the main function of the program. It starts by parsing the command line arguments to get the threshold, input file name, and output file name. Then it parses the evidence file using the `evidenceFileParser` struct, and creates a `trust.DirectReferralOpinion` using the `make` function. The final referral trust equations are created using the `equations.CreateFinalReferralTrustEquations` function. The equations are solved using `solver.SolveFinalReferralTrustEquations`. The discount values for the final referral trust are then written to the output file using the `writeFinalReferralTrustDiscount` function.

### `func parseCmdLineParams() (threshold uint64, inputFileName string, outputFileName string)`

This function parses the command line arguments to get the threshold, input file name, and output file name. It returns the parsed values.

### `func writeFinalReferralTrustDiscount(outputFileName string, context *equations.DefaultFinalReferralTrustEquationContext) (err error)`

This function writes the final referral trust discount values to the output file.

### `type evidenceFileParser struct`

This struct represents a parser for an evidence file.

### `func (p evidenceFileParser) GetEvidenceIterator() trust.EvidenceIterator`

This function returns an iterator over the evidence in the file.

### `func parseEvidenceFile(fileName string) trust.EvidenceIterator`

This function parses an evidence file and returns an iterator over the evidence.

Dependencies
------------

*   `bufio`
*   `bytes`
*   `errors`
*   `fmt`
*   `log`
*   `os`
*   `strconv`
*   `github.com/BraveNewCapital/ebsl-go/evidence`
*   `github.com/BraveNewCapital/ebsl-go/trust`
*   `github.com/BraveNewCapital/ebsl-go/trust/equations`
*   `github.com/BraveNewCapital/ebsl-go/trust/equations/solver`
