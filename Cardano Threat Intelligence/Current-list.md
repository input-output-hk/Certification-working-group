# Current List 

## [CTI-2023-ADA-1101: Datum hijacking](./Vulnerabilities/CTI-2023-ADA-11-01.md)

Whenever an output is created with a suitable datum, it might happen that the validator forgets to verify its associated address. In that case, any script with the same kind of datum could benefit from redirecting that output.

## [CTI-2023-ADA-1102: Sidechannel token name](./Vulnerabilities/CTI-2023-ADA-11-02.md)

Whenever a token is expected to appear in a minted value, it might happen that the associated minting policy forgets to check for the presence of additional tokens with different names.

## [CTI-2023-ADA-1103: Stealing validity tokens](./Vulnerabilities/CTI-2023-ADA-11-03.md)

On Cardano, tokens are often used to verify a valid state. In case of insufficient checks, a validity token can be stolen and moved to another UTxO with a spoofed datum, which can be potentially used to do unlimited damage, e.g. draining a protocol.
