[TODO]
<ul>
	<li>Check if all are pertinent for a Vulnerability list</li>
	<li>Check if there is no double entry</li>
	<li>Check if some CPVs should be merged into a one</li>
	<li>Standardize the format of the entries</li>
	<li>Provide examples?</li>
	<li>Long term: Define a process for proposing a new CVE, reviewing it and adding it to the list</li>
</ul>

[References]
<ul>
	<li>plutonimicon link</li>
	<li>MLabs audit</li>
</ul>



| ID |CPV-2023-001  |
|--|--|
| Name | UTXO Value Size Spam AKA Token Dust Attack
Description | The UTXO of too many tokens_  (or a single AssetClass with a large amount of tokens) - where a single utxo carries hundreds of unique tokens with different CurrencySymbols and/or TokenNames until it’s representation approaches the 16kb limit, this is then placed in a Validator in such a way that one or more Redeemers will need to consume this utxo, blocking transactions on that Redeemer/Validator
|Mitigations| <ul><li>A minimum ada value is required on all UTXOs, which scales with UTXO size. This may mitigate protocol tx sizes somewhat. A similar calculation could be used on-chain to produce a size heuristic.</li><li>Don’t allow arbitrary value to be put in trusted places.</li></ul>|


| ID |CPV-2023-002  |
|--|--|
| Name | Large Datum or Unbounded Protocol Datum
Description | A datum that is too big, or allowed to get increasingly big, will ultimately reach XU and/or size limits imposed by the Plutus interpreter. This could lead to Script XU, size overflow, unspendable outputs and even protocol halting |
|Mitigation| Make sure not to use infinitely sized data types, or, if needed, use and infinitely sized one and limit its size or split the datum into as many outputs as needed.


| ID |CPV-2023-003  |
|--|--|
| Name | Lack of staking control
Description | Protocols must ensure that staking is determined by the protocol for funds held by the protocol. For example, a Uniswap-style DEX must not allow users to arbitrarily change the staking address of the pool.|


| ID |CPV-2023-004  |
|--|--|
| Name | EUTXO Concurrency DoS
Description | Blocking EUTXOs could be repeatedly spent with a trivial transaction, potentially locking out a whole protocol. Even scalable solutions could be vulnerable to this in a distributed manner.|
|Mitigations| <ul><li>Extra fees/other disincentives to discourage attacks/make them disproportionately expensive/make them benefit the protocol</li><li> ‘freezing’ periods to allow protocol functions (keepers) to execute</li><ul><li>Validators can check Tx time range to have ‘cold’ periods in which only keeper functions can execute, or whole protocol can prevent progress until a keeper action is allowed to progress and update a timestamp. i.e. every x seconds, there are n seconds where only keeper transactions will validate. Or, every x seconds, the protocol cannot progress until a keeper function has been run.</li><li> Can only be done if there’s a server — and won’t work for custom transactions. Probably needs to be implemented on the Cardano side</li></ul></ul>


| ID |CPV-2023-005  |
|--|--|
| Name | PAB denial of service
Description | this covers known exploits of the plutus application backend that may result in successful DoS attacks.  Plutus relies on  `aeson`, which has a known DoS exploit listed here:  [](https://github.com/haskell/aeson/issues/864)[https://github.com/haskell/aeson/issues/864](https://github.com/haskell/aeson/issues/864)|


| ID |CPV-2023-006  |
|--|--|
| Name | Unauthorized Data modification
Description | This often comes from missing a signature or transaction validation in onchain code, mitigation is to keep a test suite where each actor fails to validate the transaction, such that this code cannot be missing.|
|Mitigation| 

| ID |CPV-2023-007  |
|--|--|
| Name | Offchain Oracle Data chain-of-information Attacks
Description | This deals more with an offchain server|
| Mitigations | <ul><li>Building production data integrations that connect with IP (mitigating DNS attacks)</li><li> Using Trusted Private Modules for transaction signatures (keeps private keys entirely within a single cpu core, helps prevent data leakage)</li></ul>


| ID |CPV-2023-008  |
|--|--|
| Name | Oracle PK Attack
Description | Cryptographic keys used by an oracle system may become a valuable point of attack
| Mitigations |<ul><li>On-chain system allowing key revoking/expiry/updating (perhaps a script which issues a single-use permission-token)</li><li> multi-sig (hard to automate this)</li><li> A more robust oracle ecosystem (as of yet non-existent on Cardano)</li></ul>


| ID |CPV-2023-009  |
|--|--|
| Name | Oracle Price Manipulation |
| Description | See [article](https://decrypt.co/49657/oracle-exploit-sees-100-million-liquidated-on-compound) for an instance of this with Compound. An attacker was able to manipulate Coinbases oracle to report a price which caused liquidations in Compound.|
| Mitigation| <ul><li>Time weighted averages</li><li>Max/Min reportable price change (can be useful for stablecoins, may be less useful for generic price information for e.g. lending platforms)</li><li>Consuming price information from many oracle sources - Coinbase, Binance, Coingecko, DEXes, etc.</li><li>Chainlink or similar (Compound now uses chainlink since the oracle attack)</li></ul>



| ID |CPV-2023-010  |
|--|--|
| Name | Infinite Mint |
| Description |This is an attack vector where an attacker finds unexpected ways to mint all kinds of tokens without the correct authorization. |
| Mitigation| |


| ID |CPV-2023-011  |
|--|--|
| Name |Parameterization |
| Description | This isn’t a vulnerability, but is more so an oversight that can lead to vulnerabilities that _should_ be obvious. On-chain, it is **highly non-trivial** (module crypto magic) to check that a script is an instantiation of some parameterized script. Off-chain, this is less true, but even then, you have to be careful that you instantiate the script manually using the `Apply` constructor of UPLC. That way, you can off-chain match on that, and check that the LHS is the parameterized script, then the RHS is the parameter itself. |
| Mitigation| |


| ID |CPV-2023-012  |
|--|--|
| Name | Other Redeemer |
| Description |<ul><li> Test: Transaction can avoid some checks when it can successfully spend a UTxO or mint a token with a redeemer that some script logic didn’t expect to be used.</li><li>Property: A validator/policy should check explicitly whether the ‘other’ validator/policy is invoked with the expected redeemer.</li><li>Impacts:<ul><li>Bypassing checks</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-013  |
|--|--|
| Name | Other Token Name |
| Description | <ul><li>Test: Transaction can mint additional tokens with some ‘other’ token name of ‘own’ currency alongside the intended token name.</li><li>Property: A policy should check that the total value minted of their ‘own’ currency symbol doesn’t include unintended token names.</li><li>Impacts:<ul><li>Stealing protocol tokens</li><li>Unauthorised protocol actions</li></li></ul></ul>|
| Mitigation| |

| ID |CPV-2023-014  |
|--|--|
| Name | Arbitrary UTxO datum |
| Description | <ul><li>Test: Transaction can create protocol UTxOs with arbitrary datums.</li><li>Property: A protocol should ensure that all protocol UTxOs hold intended datums.</li><li>Impacts:<ul><li>Script XU overflow</li><li>Unspendable outputs</li><li>Protocol halting</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-015  |
|--|--|
| Name | Unbounded protocol value |
| Description | <ul><li>Test: Transaction can create increasingly more protocol tokens in protocol UTxOs.</li><li>Property: A protocol should ensure that protocol values held in protocol UTxOs are bounded within reasonable limits.</li><li>Impacts:<ul><li>Script XU overflow</li><li>Unspendable outputs</li><li> Protocol halting</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-016  |
|--|--|
| Name | Foreign UTxO tokens |
| Description | <ul><li>Test: Transaction can create protocol UTxOs with foreign tokens attached alongside the protocol tokens.</li><li>Property: A protocol should ensure that protocol UTxOs only hold the tokens used by the protocol.</li><li>Impacts:<ul><li>Script XU overflow</li><li>Unspendable outputs</li><li>Protocol halting</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-017  |
|--|--|
| Name | Multiple satisfaction |
| Description | <ul><li>Test: Transaction can spend multiple UTxOs from a validator by satisfying burning and/or paying requirements for a single input while paying the rest of the unaccounted input value to a foreign address.</li><li>Property: A validator/policy should ensure that all burning and paying requirements consider all relevant inputs in aggregate.</li><li>Impacts:<ul><li>Stealing protocol tokens</li><li>Unauthorised protocol actions</li><li>Integrity</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-018  |
|--|--|
| Name | Locked Ada |
| Description | <ul><li>Test: Protocol locks Ada value indefinitely in obsolete validator outputs.</li><li>Property: Protocol should include mechanisms to enable redeeming any Ada value stored at obsolete validator outputs.</li><li>Impacts:<ul><li>Financial sustainability</li><li>Cardano halting</li></ul></li></ul> |
| Mitigation| |


| ID |CPV-2023-019  |
|--|--|
| Name | Locked non Ada values |
| Description | <ul><li>Test: Protocol indefinitely locks some non-Ada values that ought to be circulating in the economy.</li><li>Property: Protocol should include mechanisms to enable redeeming any non-Ada value stored at obsolete validator outputs.</li><li>Impacts:<ul><li>Financial sustainability</li><li>Protocol halting</li></ul></li></ul> |
| Mitigation| |


| ID |CPV-2023-020  |
|--|--|
| Name | Missing UTxO authentication |
| Description | <ul><li>Test: Transaction can perform a protocol action by spending or referencing an illegitimate output of a protocol validator.</li><li>  Property: All spending and referencing of protocol outputs should be authenticated.</li><li>Impacts:<ul><li>Unauthorised protocol actions</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-021  |
|--|--|
| Name | Missing incentive |
| Description |<ul><li>Test: There is no incentive for users to participate in the protocol to maintain the intended goals of the protocol.</li><li>Property: All users in the Protocol should have an incentive to maintain the intended goals of the protocol</li><li>Impacts:<ul><li>Protocol stalling</li><li>Protocol halting</li></ul></li></ul>
 |
| Mitigation| |


| ID |CPV-2023-022  |
|--|--|
| Name | Bad Incentive |
| Description | <ul><li>Test: There is an incentive for users to participate in the protocol that compromises the intended goals of the protocol.</li><li> Property: No users of the protocol should have an incentive to compromise the intended goals of the protocol.</li><li>Impacts:<ul><li>Protocol stalling</li><li>Protocol halting</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-023  |
|--|--|
| Name | UTxO contention |
| Description |<ul><li>Test: The protocol requires that transactions spend a globally shared UTxO(s) thereby introducing a contention point.</li><li>Property: The protocol should enable parallel transactions and contention-less global state management if possible.</li><li>Impacts:<ul><li>Protocol stalling</li><li>Protocol halting</li></ul></li></ul> |
| Mitigation| |


| ID |CPV-2023-024  |
|--|--|
| Name | Cheap spam |
| Description | <ul><li>Test: A transaction can introduce an idempotent or useless action/effect in the protocol for a low cost that can compromise protocol operations.</li><li>Property: The protocol should ensure that the cost for introducing a salient action is sufficient to deter spamming. Severity increases when compounded with the utxo-contention vulnerability.</li><li>Impacts:<ul><li>Protocol stalling</li><li>Protocol halting</li></ul></li></ul> |
| Mitigation| |


| ID |CPV-2023-025  |
|--|--|
| Name | Insufficient tests |
| Description | <ul><li>Test: There is piece of validation logic that tests do not attempt to verify.</li><li>Property: Every piece of validator code gets meaningfully executed during tests.</li><li>Impacts:<ul><li>Correctness</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-026  |
|--|--|
| Name | Incorrect documentation |
| Description | <ul><li>Test: There is a mistake or something confusing in existing documentation.</li><li>Property: Everything documented is clear and correct.</li><li>Impacts:<ul><li>Correctness</li><li>Maintainability</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-027  |
|--|--|
| Name | Insufficient documentation |
| Description |<ul><li>Test: There is a lack of important documentation.</li><li>Property: Everything of importance is documented.</li><li>Impacts:<ul><li>Correctness</li><li>Comprehension</li></ul></li></ul>|
| Mitigation| |


| ID |CPV-2023-0xx  |
|--|--|
| Name | Template |
| Description | |
| Mitigation| |