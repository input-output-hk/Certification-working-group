## UTXO Value Size Spam AKA Token Dust Attack

#### Description 

The UTXO of too many tokens_  (or a single AssetClass with a large amount of tokens) - where a single utxo carries hundreds of unique tokens with different CurrencySymbols and/or TokenNames until it’s representation approaches the 16kb limit, this is then placed in a Validator in such a way that one or more Redeemers will need to consume this utxo, blocking transactions on that Redeemer/Validator

### Mitigations

A minimum ada value is required on all UTXOs, which scales with UTXO size. This may mitigate protocol tx sizes somewhat. A similar calculation could be used on-chain to produce a size heuristic.

Don’t allow arbitrary value to be put in trusted places.

## Large Datum or Unbounded Protocol Datum

#### Description

A datum that is too big, or allowed to get increasingly big, will ultimately reach XU and/or size limits imposed by the Plutus interpreter. This could lead to Script XU, size overflow, unspendable outputs and even protocol halting

### Mitigation

Make sure not to use infinitely sized data types, or, if needed, use and infinitely sized one and limit its size or split the datum into as many outputs as needed.

## Lack of staking control

### Description

Protocols must ensure that staking is determined by the protocol for funds held by the protocol. For example, a Uniswap-style DEX must not allow users to arbitrarily change the staking address of the pool.

## EUTXO Concurrency DoS

### Description

Blocking EUTXOs could be repeatedly spent with a trivial transaction, potentially locking out a whole protocol. Even scalable solutions could be vulnerable to this in a distributed manner.
###  Mitigations

Extra fees/other disincentives to discourage attacks/make them disproportionately expensive/make them benefit the protocol

‘freezing’ periods to allow protocol functions (keepers) to execute:

- Validators can check Tx time range to have ‘cold’ periods in which only keeper functions can execute, or whole protocol can prevent progress until a keeper action is allowed to progress and update a timestamp. i.e. every x seconds, there are n seconds where only keeper transactions will validate. Or, every x seconds, the protocol cannot progress until a keeper function has been run.

- Can only be done if there’s a server — and won’t work for custom transactions. Probably needs to be implemented on the Cardano side

## PAB denial of service

### Description

This covers known exploits of the plutus application backend that may result in successful DoS attacks.  Plutus relies on  `aeson`, which has a known DoS exploit listed here:  [](https://github.com/haskell/aeson/issues/864)[https://github.com/haskell/aeson/issues/864](https://github.com/haskell/aeson/issues/864)

## Unauthorized Data modification

### Description

This often comes from missing a signature or transaction validation in onchain code, mitigation is to keep a test suite where each actor fails to validate the transaction, such that this code cannot be missing.

## Offchain Oracle Data chain-of-information Attacks

### Description

This deals more with an offchain server

### Mitigations

Building production data integrations that connect with IP (mitigating DNS attacks)
Using Trusted Private Modules for transaction signatures (keeps private keys entirely within a single cpu core, helps prevent data leakage)

## Oracle PK Attack

### Description

Cryptographic keys used by an oracle system may become a valuable point of attack

### Mitigations

On-chain system allowing key revoking/expiry/updating (perhaps a script which issues a single-use permission-token)
Multi-sig (hard to automate this)
A more robust oracle ecosystem (as of yet non-existent on Cardano)

## Oracle Price Manipulation

### Description

See [article](https://decrypt.co/49657/oracle-exploit-sees-100-million-liquidated-on-compound) for an instance of this with Compound. An attacker was able to manipulate Coinbases oracle to report a price which caused liquidations in Compound.

### Mitigations

- Time weighted averages
- Max/Min reportable price change (can be useful for stablecoins, may be less useful for generic price information for e.g. lending platforms)
- Consuming price information from many oracle sources - Coinbase, Binance, Coingecko, DEXes, etc.
-Chainlink or similar (Compound now uses chainlink since the oracle attack)

## Infinite Mint

### Description

This is an attack vector where an attacker finds unexpected ways to mint all kinds of tokens without the correct authorization.

## CPV-2023-011:Parameterization

### Description

This isn’t a vulnerability, but is more so an oversight that can lead to vulnerabilities that _should_ be obvious. On-chain, it is **highly non-trivial** (module crypto magic) to check that a script is an instantiation of some parameterized script. Off-chain, this is less true, but even then, you have to be careful that you instantiate the script manually using the `Apply` constructor of UPLC. That way, you can off-chain match on that, and check that the LHS is the parameterized script, then the RHS is the parameter itself.

## Other Redeemer

### Description

- Test: Transaction can avoid some checks when it can successfully spend a UTxO or mint a token with a redeemer that some script logic didn’t expect to be used.
- Property: A validator/policy should check explicitly whether the ‘other’ validator/policy is invoked with the expected redeemer.

### Impacts

Bypassing checks

## Other Token Name

### Description

- Test: Transaction can mint additional tokens with some ‘other’ token name of ‘own’ currency alongside the intended token name.
- Property: A policy should check that the total value minted of their ‘own’ currency symbol doesn’t include unintended token names.

### Impacts

- Stealing protocol tokens
- Unauthorised protocol actions

## Arbitrary UTxO datum

### Description

- Test: Transaction can create protocol UTxOs with arbitrary datums.
- Property: A protocol should ensure that all protocol UTxOs hold intended datums.

### Impacts

- Script XU overflow
- Unspendable outputs
- Protocol halting

## Unbounded protocol value

### Description

- Test: Transaction can create increasingly more protocol tokens in protocol UTxOs.
- Property: A protocol should ensure that protocol values held in protocol UTxOs are bounded within reasonable limits.

### Impacts

- Script XU overflow
- Unspendable outputs
- Protocol halting


## Foreign UTxO tokens

### Description

- Test: Transaction can create protocol UTxOs with foreign tokens attached alongside the protocol tokens.
- Property: A protocol should ensure that protocol UTxOs only hold the tokens used by the protocol.

### Impacts

- Script XU overflow
- Unspendable outputs
- Protocol halting


## Multiple satisfaction

### Description

- Test: Transaction can spend multiple UTxOs from a validator by satisfying burning and/or paying requirements for a single input while paying the rest of the unaccounted input value to a foreign address.
- Property: A validator/policy should ensure that all burning and paying requirements consider all relevant inputs in aggregate.

### Impacts

- Stealing protocol tokens
- Unauthorised protocol actions
- Integrity


## Locked Ada

### Description

- Test: Protocol locks Ada value indefinitely in obsolete validator outputs.
- Property: Protocol should include mechanisms to enable redeeming any Ada value stored at obsolete validator outputs.

### Impacts:
- Financial sustainability
- Cardano halting

## Locked non Ada values

### Description

- Test: Protocol indefinitely locks some non-Ada values that ought to be circulating in the economy.
- Property: Protocol should include mechanisms to enable redeeming any non-Ada value stored at obsolete validator outputs.

### Impacts

- Financial sustainability
- Protocol halting

## Missing UTxO authentication

### Description

- Test: Transaction can perform a protocol action by spending or referencing an illegitimate output of a protocol validator.
- Property: All spending and referencing of protocol outputs should be authenticated.

### Impacts

- Unauthorised protocol actions

## Missing incentive

### Description

- Test: There is no incentive for users to participate in the protocol to maintain the intended goals of the protocol.
- Property: All users in the Protocol should have an incentive to maintain the intended goals of the protocol

### Impacts:

- Protocol stalling
- Protocol halting

## Bad Incentive

### Description

- Test: There is an incentive for users to participate in the protocol that compromises the intended goals of the protocol.
- Property: No users of the protocol should have an incentive to compromise the intended goals of the protocol.

### Impacts

- Protocol stalling
- Protocol halting

## UTxO contention

### Description

- Test: The protocol requires that transactions spend a globally shared UTxO(s) thereby introducing a contention point.
- Property: The protocol should enable parallel transactions and contention-less global state management if possible.

### Impacts

- Protocol stalling
- Protocol halting

## Cheap spam

### Description

- Test: A transaction can introduce an idempotent or useless action/effect in the protocol for a low cost that can compromise protocol operations.
- Property: The protocol should ensure that the cost for introducing a salient action is sufficient to deter spamming. Severity increases when compounded with the utxo-contention vulnerability.

### Impacts

- Protocol stalling
- Protocol halting

## Insufficient tests

### Description

- Test: There is piece of validation logic that tests do not attempt to verify.
- Property: Every piece of validator code gets meaningfully executed during tests.

### Impacts

Correctness

## Incorrect documentation

### Description

- Test: There is a mistake or something confusing in existing documentation.
- Property: Everything documented is clear and correct.

### Impacts

- Correctness
- Maintainability

## Insufficient documentation

### Description

- Test: There is a lack of important documentation.
- Property: Everything of importance is documented.

### Impacts

- Correctness
- Comprehension
