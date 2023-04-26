# CTI-2023-ADA-1102: Sidechannel token name

## Author

Tweag -- High Assurance Software Group.

### Summary

Whenever a token is expected to appear in a minted value, it might happen that the associated minting policy forgets to check for the presence of additional tokens with different names.

### Description

This vulnerability occurs when a user forgets to check for the presence of other token names within a given minting policy, only checking for the right amount of a given token name. In that case, any other token could possibly be minted within the same minting policy.

### Risk Assessment

- **Likelihood:** **Low** 
- **Difficulty:** **Low**
- **Impact:** **High**
- **Severity:** **High**

### Steps to Reproduce

Assuming a minting policy is vulnerable this sidechannel token name issue, any user can issue transaction with additional tokens minted with various names and similar currency symbol.

### Technical Details

Here is an example of a vulnerable check in a minting policy: `Pl.assetClassValueOf v (cur, tok) == 1`.

### Mitigation & Remediation Steps

One needs to ensure that the whole component of the minted value that is associated with the current minting policy is exactly equal to what is expected, instead of only considering a specific token name.

### References

This vulnerability was found in MinSwap, as depicted [here](https://www.tweag.io/blog/2022-03-25-minswap-lp-vulnerability/).
