| ID |CPV-2023-001  |
|--|--|
| Name | UTXO Value Size Spam AKA Token Dust Attack
Description | The UTXO of too many tokens_  (or a single AssetClass with a large amount of tokens) - where a single utxo carries hundreds of unique tokens with different CurrencySymbols and/or TokenNames until it’s representation approaches the 16kb limit, this is then placed in a Validator in such a way that one or more Redeemers will need to consume this utxo, blocking transactions on that Redeemer/Validator
|Mitigations| <ul><li>A minimum ada value is required on all UTXOs, which scales with UTXO size. This may mitigate protocol tx sizes somewhat. A similar calculation could be used on-chain to produce a size heuristic.</li><li>Don’t allow arbitrary value to be put in trusted places.</li></ul>|

##

| ID |CPV-2023-002  |
|--|--|
| Name | Large Datum size
Description | The Datum of too much size - similarly, Datum on a UTXO which is of an inappropriately large size which _needs_ to be consumed for a transaction on a critical redeemer to succeed.|
|Mitigation| Make sure not to use infinitely sized data types, or take and infinitely sized one and limit it in some way.

##

| ID |CPV-2023-003  |
|--|--|
| Name | Lack of staking control
Description | Protocols must ensure that staking is determined by the protocol for funds held by the protocol. For example, a Uniswap-style DEX must not allow users to arbitrarily change the staking address of the pool.|

##

| ID |CPV-2023-004  |
|--|--|
| Name | EUTXO Concurrency DoS
Description | Blocking EUTXOs could be repeatedly spent with a trivial transaction, potentially locking out a whole protocol. Even scalable solutions could be vulnerable to this in a distributed manner.|
|Mitigations| <ul><li>Extra fees/other disincentives to discourage attacks/make them disproportionately expensive/make them benefit the protocol</li><li> ‘freezing’ periods to allow protocol functions (keepers) to execute</li><ul><li>Validators can check Tx time range to have ‘cold’ periods in which only keeper functions can execute, or whole protocol can prevent progress until a keeper action is allowed to progress and update a timestamp. i.e. every x seconds, there are n seconds where only keeper transactions will validate. Or, every x seconds, the protocol cannot progress until a keeper function has been run.</li><li> Can only be done if there’s a server — and won’t work for custom transactions. Probably needs to be implemented on the Cardano side</li></ul></ul>

##

| ID |CPV-2023-005  |
|--|--|
| Name | PAB denial of service
Description | this covers known exploits of the plutus application backend that may result in successful DoS attacks.  Plutus relies on  `aeson`, which has a known DoS exploit listed here:  [](https://github.com/haskell/aeson/issues/864)[https://github.com/haskell/aeson/issues/864](https://github.com/haskell/aeson/issues/864)|

##

| ID |CPV-2023-006  |
|--|--|
| Name | Unauthorized Data modification
Description | This often comes from missing a signature or transaction validation in onchain code, mitigation is to keep a test suite where each actor fails to validate the transaction, such that this code cannot be missing.|
|Mitigation| 

##

| ID |CPV-2023-007  |
|--|--|
| Name | Offchain Oracle Data chain-of-information Attacks
Description | This deals more with an offchain server|
| Mitigations | <ul><li>Building production data integrations that connect with IP (mitigating DNS attacks)</li><li> Using Trusted Private Modules for transaction signatures (keeps private keys entirely within a single cpu core, helps prevent data leakage)</li></ul>

##

| ID |CPV-2023-008  |
|--|--|
| Name | Oracle PK Attack
Description | Cryptographic keys used by an oracle system may become a valuable point of attack
| Mitigations |<ul><li>On-chain system allowing key revoking/expiry/updating (perhaps a script which issues a single-use permission-token)</li><li> multi-sig (hard to automate this)</li><li> A more robust oracle ecosystem (as of yet non-existent on Cardano)</li></ul>

##
| ID |CPV-2023-009  |
|--|--|
| Name | Oracle Price Manipulation |
| Description | See [article](https://decrypt.co/49657/oracle-exploit-sees-100-million-liquidated-on-compound) for an instance of this with Compound. An attacker was able to manipulate Coinbases oracle to report a price which caused liquidations in Compound.|
| Mitigation| <ul><li>Time weighted averages</li><li>Max/Min reportable price change (can be useful for stablecoins, may be less useful for generic price information for e.g. lending platforms)</li><li>Consuming price information from many oracle sources - Coinbase, Binance, Coingecko, DEXes, etc.</li><li>Chainlink or similar (Compound now uses chainlink since the oracle attack)</li></ul>

##
| ID |CPV-2023-010  |
|--|--|
| Name | Infinite Mint |
| Description |This is an attack vector where an attacker finds unexpected ways to mint all kinds of tokens without the correct authorization. |
| Mitigation| |

##
| ID |CPV-2023-011  |
|--|--|
| Name |Parameterization |
| Description |This isn’t a vulnerability, but is more so an oversight that can lead to vulnerabilities that _should_ be obvious. On-chain, it is **highly non-trivial** (module crypto magic) to check that a script is an instantiation of some parameterized script. Off-chain, this is less true, but even then, you have to be careful that you instantiate the script manually using the `Apply` constructor of UPLC. That way, you can off-chain match on that, and check that the LHS is the parameterized script, then the RHS is the parameter itself. |
| Mitigation| |


##
| ID |CPV-2023-0xx  |
|--|--|
| Name |  |
| Description | |
| Mitigation| |