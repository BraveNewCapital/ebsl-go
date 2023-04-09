Package trust provides a library for calculating trust and reputation scores based on direct and referral trust.

### Types

*   `Link`: Represents the trust direction. Each link consists of two nodes represented by their unique identifiers (uint64).
    
*   `DirectReferralEvidence`: Represents the direct referral trust matrix in the evidence space. It is a map of links to evidence types.
    
*   `DirectReferralOpinion`: Represents the direct referral trust matrix in the opinion space. It is a map of links to opinion types.
    
*   `DirectFunctionalTrust`: Represents the direct opinion about an entity's ability to provide a specific function. It is a map of entity IDs to opinion types.
    
*   `FinalReferralOpinion`: Represents the final referral trust matrix in the opinion space. It is a map of links to opinion types.
    
*   `NextLinkHandler`: Defines a function that handles the next link in a link iterator and returns an error.
    
*   `NextEvidenceHandler`: Defines a function that handles the next evidence in an evidence iterator and returns an error.
    
*   `LinkIterator`: Defines a function that iterates over all links and applies the provided handler to each link.
    
*   `EvidenceIterator`: Defines a function that iterates over all evidences and applies the provided handler to each evidence.
    
*   `IterableLinks`: Defines an interface that allows iterating over all links.
    
*   `IterableEvidences`: Defines an interface that allows iterating over all evidences.
    

### Functions

*   `func (l Link) String() string`: Implements the `fmt.Stringer` interface for the `Link` type.
    
*   `func (dre DirectReferralEvidence) GetLinkIterator() LinkIterator`: Implements the `IterableLinks` interface for the `DirectReferralEvidence` type.
    
*   `func (dre DirectReferralEvidence) GetEvidenceIterator() EvidenceIterator`: Implements the `IterableEvidences` interface for the `DirectReferralEvidence` type.
    
*   `func (dro DirectReferralOpinion) FromIterableEvidences(evidences IterableEvidences, c uint64) DirectReferralOpinion`: Builds the `DirectReferralOpinion` from the given `IterableEvidences`.
    
*   `func (dro DirectReferralOpinion) GetLinkIterator() LinkIterator`: Implements the `IterableLinks` interface for the `DirectReferralOpinion` type.
    
*   `func (dre DirectReferralEvidence) ToDirectReferralOpinion(c uint64) DirectReferralOpinion`: Transforms the `DirectReferralEvidence` to the `DirectReferralOpinion`.
    

### Types and Functions Explained

The `Link` type represents the trust direction. Each `Link` consists of two nodes represented by their unique identifiers (`uint64`).

The `DirectReferralEvidence` type represents the direct referral trust matrix in the evidence space. It is a map of links to evidence types. The `DirectReferralOpinion` type represents the direct referral trust matrix in the opinion space. It is a map of links to opinion types. The `DirectFunctionalTrust` type represents the direct opinion about an entity's ability to provide a specific function. It is a map of entity IDs to opinion types. The `FinalReferralOpinion` type represents the final referral trust matrix in the opinion space. It is a map of links to opinion types.

The `NextLinkHandler` and `NextEvidenceHandler` types define functions that handle the next link or evidence in a link or evidence iterator and return an error, respectively.

The `LinkIterator` and `EvidenceIterator` types define functions that iterate over all links or evidences and apply the provided handler to each link or evidence, respectively.

The `IterableLinks` and `IterableEvidences` types define interfaces that allow iterating over all links
