# Vulnerabilities from audits

## AADA (Only critical ones)

### Borrower/Lender tokens do not have to be NFTs

### Double Satisfaction - Collateral

**WG** Reads close to [Multiple satisfaction](./full-list-to-be-triaged.md)

### Double Satisfaction - Loan

**WG** Reads close to [Multiple satisfaction](./full-list-to-be-triaged.md)

### Resource DoS attack

**WG** Reads close to [Foreign UTxO tokens](./full-list-to-be-triaged.md)

### Lender can take collateral when providing loan

### Lender can take the whole collateral in liquidation after deadline

### Inability to stop a compromised oracle node

**WG** Reads close to [Offchain Oracle Data chain-of-information Attacks](./full-list-to-be-triaged.md)

### Oracle price consensus uncertainty

**WG** Reads close to [Oracle Price Manipulation](./full-list-to-be-triaged.md), maybe we should consider an extended weakness 

### Attacker can spoof AADA NFTs and impersonate their rightful holders

**WG** Is it close to [Infinite Mint](./full-list-to-be-triaged.md)?

### Lender can liquidate and take the whole collateral as soon as he lends

### Borrower is not able to repay the loan and loses the collateral

## Artifct (only Major)

### A “double satisfaction” vulnerability

**WG** Reads close to [Multiple satisfaction](./full-list-to-be-triaged.md)

### Possible missing assets when purchasing

**WG** Is it a case of [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)

### Seller price 1 Ada too low with zero percent royalties

**WG** Sounds like a functional issue, I think.

### Price is not enforced with reused royalty address

**WG** Sounds like a functional issue, I think.


## Indigo Protocol (Only High severity)

### Unauthorized Manipulation of StakingManager

An attacker can counterfeit a StakingPosition(1) output and use StakingToken
(issue #4) to make it seem authentic. The attacker then can un-stake his counterfeit
StakingPosition output and decreases totalStake in StakingManager(2) output.
If the totalStake is low enough, the attacker can propose, pass, and execute any
proposals he or she wants.
This problem will be resolved by fxing issue #4 (StakingToken can be duplicated).
With the release of Plutus V2.0, we are able to view all redeemers from the Script
Context, which will help us simplify our Validator Scripts(3) and Minting Policies(4)
while avoiding more security problems. The better design will be implemented
immediately after that.

**WG** Issue 4 (below) is about the StakingToken being duplicated so is this related to [CTI-2023-ADA-1103: Stealing validity tokens](./Vulnerabilities/CTI-2023-ADA-11-03.md) or [Infinite Mint](./full-list-to-be-triaged.md)?

### Stability Pool reward cannot be withdrawn

The validator responsible for the Stability Pool(5) always fails, not allowing users to
withdraw their rewards. There is confusion when checking to block users withdraw a
negative amount.

**WG** Could it be in a "Locked funds" weakness/vulnerability?

### Protocol parameters cannot be modifed

One line of validator code requires the transaction must burn one INDY token. But
INDY tokens can not be burned so users have no way to execute the proposals to
modify protocol parameters.

**WG** Sounds like a functional issue?

### StakingToken can be duplicated

**WG** [CTI-2023-ADA-1103: Stealing validity tokens](./Vulnerabilities/CTI-2023-ADA-11-03.md) or [Infinite Mint](./full-list-to-be-triaged.md)?

### Modifying proposalDeposit interacts with exising proposals

**WG** From the text, maybe a function issue that should have been caught with proper complete testing.

## JPG.store (Only P1 severity)

### Negative values in payout may cause token buyers to pay more than the listing price

**WG** From the text, maybe a function issue that should have been caught with proper complete testing.

### The buyer of a listed token may not receive the token

**WG** From the text, maybe [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)?

### The seller may not get the fair amount of Ada for the sell

**WG** From the text, maybe [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)?

## MinSwap (Only critical severity)

### Unauthorized Redeeming of Open Orders

Open orders can be redeemed by anybody with the ApplyOrder redeemer as long as the attacker also
redeems one output belonging to the address of the poolCode validator. This can be easily done by redeeming any pool with profit-sharing enabled with WithdrawLiquidity. This way attackers can steal the funds locked in open orders.

### LP Tokens Can Be Duplicated

**WG** [Infinite Mint](./full-list-to-be-triaged.md)?

### Unauthorized Hijacking of Pools Funds

**WG** [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)?

## Muesli Swap (Only P1 severity)

### Double satisfaction attack

**WG** [Multiple satisfaction](./full-list-to-be-triaged.md)

### Inverted logic in validPartial allows buying for pennies

This is quite a fatal attack. Consider an r that is as small as possible, i.e. morally 1/∞. In such a case, justBought and justSold will be tiny, and only a tiny amount will be bought and sold. However, as it is a partial match, there must be exactly one continuing output corresponding to this order. On line 202, it is asserted that the new order is equivalent to the old one, except for oBuyAmount. oBuyAmount is such that new = old * r. This is incorrect, as the resulting ratio of what is to be sold and bought will be different for the new order relative to the original order. The lower r is, the lower the amount of buyToken to be bought will be in the new order.

**WG** Error in the logic, missing test cases?

## Optim (only Critical Severity)

### Pools can be emptied by matching a small bond

### Pools can be emptied by matching a bond with the cancel redeemer

### Funds can be locked after datum tampering

**WG** [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)?

### Bond tokens can be stolen after datum tampering

**WG** [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)?

### Bond tokens can be redeemed with different pool tokens

From the text: As mentioned in issue 2.3.1.6, an attacker can create a pool, and redirect the pool tokens to their public key address instead of paying them to a script. After doing this, an attacker can buy exactly one pool token from a different pool. Then, the attacker can redeem that pool token while tampering with the ClosedPool datum, changing the pool token in the datum to the pool token of the pool the user originally created.

**WG** [Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)? But not alone, I think.

## SundaeSwap

### Minting of unlimited number of sundae tokens

**WG** [Infinite Mint](./full-list-to-be-triaged.md)?

### Accumulation of rounding errors when exchanging old liquidity tokens for new liquidity tokens

The scaleInteger function in onchain/Sundae/Contracts/Common.hs uses the
round function provided by PlutusTx.Ration.hs to convert the Rational value to an
Integer value. However, the round function rounds up when the fraction part is greater
than or equal to 0.5 and rounds down otherwise. It could be possible that if the fraction
part is greater than or equal to 0.5, the contract returns 1 more token to the user and
this effect could accumulate and may cause the last user to receive far less than
expected amount.

**WG** Insufficient testing?

### Any tokens with the currency symbol as the hash of poolMintingPolicyContract can be minted

**WG** [Infinite Mint](./full-list-to-be-triaged.md)?

### Scooper could redeem more than the maximum number of scooper rewards

The pool contract does not check the positivity of scoopFee in EscrowDatum and pays
the sum of all the scoop fee to scooperFeeContract. If an escrow input with negative
scoopFee is included, then much less than the actual scoop fee would be paid to the
scooper fee contract and the lesser amount is paid to the scooper directly. After that the
scooper can redeem the scoop fee from the scooper fee contract. In total the scooper
can gain all the fees and circumvent the constraint that only a maximum scooper fee
shall be redeemed by scooper.

### Potential unauthorized script upgrade

Line 315 at the proposalContract only checks that the upgrade authentication token
is present but does not check how many tokens are in the UTXO. This line should also
check that the number of authentication tokens is 1. If let's say two tokens are included
in the proposal UTXO, an attacker can pay one of the tokens to itself and modify the
datum and pay it back into the proposalContract. So he can achieve an
unauthenticated upgrade to the contracts.
Although it is considered a bug of the governance system if more than 1 tokens are
given to the UTXO. But to prevent the ripple effect of such bugs in the governance
system, we would better have the check here.

### Assets in escrow contract can be stolen when upgrading pool

The UTXOs locked in escrowContract can be spent when a pool token is present. It
does not restrain how the assets in UTXO can be spent. The pool token can be spent
when upgrading a pool, which has checks to ensure that there is an update to the pool
token. So when upgrading the pool, an attacker can also spend the UTXO in
escrowContract so as to steal the assets.

### Integer division is used multiple times in computation of token amount

**WG** Sounds general enough to be (almost) its own weakness

### Assets in escrow contract can be stolen when redeeming liquidity tokens
The UTXOs locked in escrowContract can be spent when a pool token is present. It
does not restrain how the assets in UTXO can be spent. The (old) pool token is locked
by the deadPoolContract after the pool upgrade. The deadPoolContract allows
holders of old liquidity tokens to redeem for the new liquidity tokens for the new pool. An
attacker who holds some old liquidity tokens can also spend the UTXO in
escrowContract so as to steal the assets when redeeming against the
deadPoolContract.

### Less escrow riders are returned when multiple escrows from the same trader are scooped in a transaction

An escrow input must contain the correct amount of tokens regarding the type of the
order and a 2 ADA rider. The rider shall be spent back to the trader. However, if multiple
escrow inputs (n>=2) from the same trader are scooped in the same transaction, only a
single 2 ADA rider is required to be spent back to the trader. This results in 2*(n-1)
ADAs taken by the scooper from the trader.

