Given the mind-boggling complexities of the fast-evolving Cardano infrastructure (new platforms, new languages, new tools and new protocols) and the risks associated with deploying smart contracts managing millions of dollars, there are so many things to get right with smart contracts that it is easy to miss a few checks, make incorrect assumptions or fail to consider potential situations. Therefore, smart contract experts need checklists and in this issue we'll build together the checklist for certification of a Dapp.

## Checklist

1. Specification analysis (Manual)
2. Documentation analysis (Manual)
3. Testing (Automated)
4. Static analysis (Automated)
5. Fuzzing (Automated)
6. Symbolic checking (Automated)
7. Formal verification (Automated)
8. Manual analysis (manual)

## The Checklist In Details

### Specification Analysis (Manual)

Specification describes in detail what (and sometimes why) the project and its various components are supposed to do functionally as part of their design and architecture.

1. From a security perspective, it specifies what the assets are, where they are held, who are the actors, privileges of actors, who is allowed to access what and when, trust relationships, threat model, potential attack vectors, scenarios and mitigation.

2. Analyzing the specification of a project provides auditors with the above details and lets them evaluate the assumptions made and indicate any shortcomings.

3. Very few smart contract projects have detailed specifications at their first audit stage. At best, they have some documentation about what is implemented. Auditors spend a lot of time inferring specification from documentation/implementation which leaves them with less time for vulnerability assessment.

### Documentation Analysis (Manual)

Documentation is a description of what has been implemented based on the design and architectural requirements.

1. Documentation answers ‘how’ something has been designed/architected/implemented without necessarily addressing the ‘why’ and the design/requirement goals.

2. Documentation is typically in the form of Readme files in the GitHub repository describing individual contract functionality combined with functional `haddock` and individual code comments.

3. Documentation in many cases serves as a substitute for specification and provides critical insights into the assumptions, requirements and goals of the project team.

4. Understanding the documentation before looking at the code helps auditors save time in inferring the architecture of the project, contract interactions, program constraints, asset flow, actors, threat model and risk mitigation measures.

5. Mismatches between the documentation and the code could indicate stale/poor documentation, software defects or security vulnerabilities.

6. Auditors are expected to encourage the project team to document thoroughly so that they do not need to waste their time inferring this by reading code.

### Testing (Automated)

Software testing or validation is a well-known fundamental software engineering primitive to determine if software produces expected outputs when executed with different chosen inputs.

1. Smart contract testing has a similar motivation but is arguably more complicated despite their relatively smaller sizes (in lines of code) compared to Web2 software.

2. Since smart contract development inside Cardano is heavily done by Haskell, current tools are in fact Haskell testing tools but there are tools under development for Plutus solely with different levels of support for testing.

3. At the moment testing integrations and composability of main-net contracts with states and state changing, without PAB or a front-end, is non-trivial or hard to do.

4. Test coverage and test cases give a good indication of project maturity and also provide valuable insights to auditors into assumptions/edge-cases for vulnerability assessments.

5. Auditors should expect a high-level of testing and test coverage because this is a must-have software-engineering discipline, especially when smart contracts that are by-design exposed to everyone on the blockchain end up holding assets worth tens of millions of dollars.

6. "Program testing can be used to show the presence of bugs, but never to show their absence!” - E.W. Dijkstra

### Static Analysis (Automated)

Static analysis is a technique of analyzing program properties without actually executing the program.

1. This is in contrast to software testing where programs are actually executed/run with different inputs.

2. Static analysis typically is a combination of control flow and data flow analyses.

### Fuzzing (Automated)

Fuzz testing is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program. The program is then monitored for exceptions such as crashes, failing built-in code assertions.

1. Fuzzing is especially relevant to smart contracts because anyone can interact with them on the blockchain with random inputs without necessarily having a valid reason or expectation (arbitrary byzantine behavior)

### Symbolic Checking (Automated)

[Symbolic checking](https://en.wikipedia.org/wiki/Model_checking#Symbolic_model_checking) is a technique of checking for program correctness, i.e. proving/verifying, by using symbolic inputs (Datum or Redeemer) to represent set of states and transitions instead of enumerating individual states/transitions separately.

### Formal Verification (Automated)

[Formal verification](https://en.wikipedia.org/wiki/Formal_verification): is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification or property, using formal methods of mathematics

1. Formal verification is effective at detecting complex bugs which are hard to detect manually or using simpler automated tools.

2. Formal verification needs a specification of the program being verified and techniques to translate/compare the specification with the actual implementation.

### Manual Analysis (manual)

Manual analysis: is complimentary to automated analysis using tools and serves a critical need in smart contract audits

1. Automated analysis using tools is cheap (typically open-source free software), fast, deterministic and scalable (varies depending on the tool being semi-/fully-automated) but however is only as good as the properties it is made aware of, which is typically limited to Haskell related constraints.

2. Manual analysis with humans, in contrast, is expensive, slow, non-deterministic and not scalable because human expertise in smart contact security is a rare/expensive skill set today and we are slower, prone to error and inconsistent.

3. Manual analysis is however the only way today to infer and evaluate business logic and application-level constraints which is where a majority of the serious vulnerabilities are being found.

## Note

- The steps/items of the checklist, tagged with either manual or automated, which means the step can be done with tools, whether the tool for that purpose exist or not.

- whether the checklist is applicable for what layer exactly is an open question.

- About ***Symbolic checking*** to me personally it is not clear how can we do it inside cardano with UTxO model. Maybe `EmulatorTrace` is the tool?

- This message will get updated when new items need to be added or removed.

### Tokenomics Analysis (Manual)
It is the study and analysis of the economics of a token, or "native asset," from its qualities to its distribution, from its production to its utilities, from its on-chain data and metadata specification to its off-chain representation, and much more. The audit process will vary based on the token being fungible or non-fungible. Also, it is necessary to mention that since the **Babel Fee** protocol and its implementation are coming to the Cardano blockchain, the analysis and audit of the tokenomics of a Dapp would have an impact on the network itself, so it should be considered whether a token is suitable to be used for the Babel Fee or not. 
Factors affecting tokens:
1. Nature of the token
   1. Layer 1
       - It is necessary to determine whether the token has standalone value on the settlement layer or if it is just a representation of another coin or token from another blockchain or sidechain of Cardano. In either case, they will settle every transaction on the network in the future using the Babel Fee protocol.
   2. Layer 2
      - Layer 2 tokens are mostly designed to help scale Dapps in a network, so how they are related to the Dapp layer 1 token must be specified.
   3. Fungible tokens
       - Fungibility is the main property of this kind of native asset, but it is important to know whether the policy ID of the token is locked or not, although this is important for non-fungible tokens as well.
   4. Non-Fungible Tokens
      - NFTs are supposedly unique, and each doesn’t have the same value, so it must be verified that those NFTs are indeed unique.
      - With the tokenization of assets such as artwork, furniture, and real estate, NFTs are basically physical items held digitally, so it should be possible to verify that the asset and its corresponding item are 1 to 1.
   5. Utility tokens
      - With the rise of DAOs on Cardano, utility tokens of DAOs, such as governance tokens, reputation tokens, contribution tokens, etc., must be regulated in such a way that when a new community member wants to join the DAO, everything is transparent, clear, and easy to understand.
2. Distribution and allocation of tokens:
   1. By Mining
   2. Pre-mined
   3. Fair Lunch
   4. IDO/ICO
3. Supply of tokens and emission schedule
   1. Circulating supply
   2. Total supply
   3. Max supply
4. Market Capitalization of a Token
5. Token model
   1. Inflationary mechanism
   2. Deflationary mechanism
   3. Duel or more tokens (utility, security, etc.)
6. Price Stability
   1. Fiat-stablecoin
   2. Crypto-stablecoin

Sure, there is more information about analysing tokenomics that must be considered for certification, but if we decide to add it to the checklist, we can discuss it deeply and thoroughly.