---
CIP: ?
Title: Certification Metdata
Category: Metadata
Status: Proposed
Authors:
    - Romain Soulat <romain.soulat@iohk.io>
Implementors: []
Discussions:
    - https://github.com/cardano-foundation/cips/pulls/??
Created: 2023-02-23
License: CC-BY-4.0
---


## Abstract
Certification is the process of providing various kinds of assurance of DApps through the provision of verifiable, trustworthy metadata linking to relevant evidence of assurance, such as audit reports, test run data, formal verification proofs etc.

Currently, certification does not have a standardised way to be stored and presented to all stakeholders (DApp developer, DApp stores, end-users, auditors, ...) in an immutable, persistent and verifiable way.

This CIP descibes a standardised method for certificates to be published and stored on-chain and for stakeholders to be able to verify the different claims of this certificate.

This proposal describes how certification metadata can be designed for DApp registration. It first describes the requirements for DApp certification, and then sets out the options for its inclusion in CIP-72.



## Motivation: why is this CIP necessary?
<!-- A clear explanation that introduces the reason for a proposal, its use cases and stakeholders. If the CIP changes an established design then it must outline design issues that motivate a rework. For complex proposals, authors must write a Cardano Problem Statement (CPS) as defined in CIP-9999 and link to it as the `Motivation`. -->

It is expected that evidence of various kinds of assurance of DApps is recorded in an immutable and verifiable way on the Cardano blockchain; these forms of assurance are: automated testing, including property-based testing (level 1), audit (level 2) and formal verification (level 3).

The metadata should be discoverable by all certification stakeholders, including end-users, DApp developers, and ecosystem components, such as light wallets and DApp stores. Information should be indexable by certification provider, DApp developer, DApp and DApp version.

### Use-cases and Stakeholders
DApp developers will seek certification from one of the providers, according to their desired level of certification and will refer to the certificate on several platforms (e.g. on their website or in their DApp registration on a DApp store).

Certification is to be provided by certification providers including: testing services (level 1), auditors (level 2), and verification services (level 3). Certification providers will issue these certificates refering to a particular version of a DApp that has succesfully gone through a certification process. 

DApp stores and light wallets will be able to pull DApps information from DApps registration or chain exploring and will link a DApp to a corresponding set of certificates.

End-user will interact with a DApp through a wallet and will be able to check the different certificates obtained by the DApp.


## Specification
<!-- The technical specification should describe the proposed improvement in sufficient technical detail. In particular, it should provide enough information that an implementation can be performed solely on the basis of the design in the CIP. This is necessary to facilitate multiple, interoperable implementations. -->

### Certification providers
Certification providers will present which level of certification was reached and present evidence of the work done. Certification providers will sign the certificate to attest that they have done the work and prevent certificate forgeries.


### Definitions
- **test** - 
- **dApp** - A decentralised application that is described by the combination of metadata, certificate and a set of used scripts.
- **dApp Store** - A dApp aggregator application which follows on-chain data looking for and verifying dApp metadata claims, serving their users linked dApp metadata.


### Properties
*`subject`*: Identifier of the claim subject (i.e dApp). A UTF-8 encoded string. Shall be the same as the one used when registering the DApp.
*`certLevel`*: Level of certification. Integer, shall be 1, 2, or 3 and shall refers to the certification standards level as defined by the Certification Working Group [Add link].
*`certificateIssuer`*: Name of the certificate issuer.
*`scriptHashes`*: Ordered complete list of script hashes for the certified DApp.

### Example
```json
{
    "subject":              "ABCDEFG1234ABCD", // DApp store needs to ensure the uniqueness of this subject 
    "certLevel":            1,
    "certificateIssuer":    "Audit House",
    "reportURLs": [
        "https://audithouse.io/certificate.pdf",
        "ipfs://bafybeiemxf5abjwjbikoz4mc3a3dla6ual3jsgpdr4cjr3oz3evfyavhwq"
    ]

    "scriptHashes": [
        "0ac61bc5d90aff9dbbc3b1fdeb3650067bf9a6c33598501ab9e68721",
        "67bfced3e447c368779ba07d609478f6598aeb6bc1b719bc4e405ea7",
        "a5bff83524f65bd0f7a2efffbc5afc476abf51f362dc1f541a4233fa",
        "f0acbc5ceeff9fa55634b159494d63980f25134b6a0b90c96fb8c7ed",
        "f22349b7611cda615a9b166aef01634a63fc40fdd98fbd1eca2b54e3",
    ],
}
```

[TBD: on/off chain, even useful?]
```json
{
    "compiler": "", // compiler + version, optimizers? compilation options?
    "auditSummary": "" // A summary (max 100 words) that can be displayed by the stores
    "certificationArtifacts": ["", ""] // links to all the certification artifacts test runs, formal proof objects, certification compilation proof object etc.
    "verificationTools": "",
    "repository": "",
    "scriptParameters": "", 
}
```

Certification metadata should be signed by the certification provider. It is assumed that certification providers make available their public keys for signature verification.

The metadata should be discoverable by all certification stakeholders, including end-users, DApp developers, and ecosystem components, such as light wallets and DApp stores. Information should be indexable by certification provider, DApp developer, DApp and DApp version.

It should be possible for there to be multiple versions of metadata published by the same certification provider for the same version of a DApp, particularly when a (minor) update of the evidence is necessary. In such a case it should be possible to identify the most recent version of the report for that DApp version. It will also be the case that the same DApp may have certification metadata provided by multiple different certification providers.

It should be possible for wallets to identify to users the certification status of a DApp when they are signing a transaction that is being submitted to a deployed DApp.

## Rationale: how does this CIP achieve its goals?
<!-- The rationale fleshes out the specification by describing what motivated the design and what led to particular design decisions. It should describe alternate designs considered and related work. The rationale should provide evidence of consensus within the community and discuss significant objections or concerns raised during the discussion.

It must also explain how the proposal affects the backward compatibility of existing solutions when applicable. If the proposal responds to a CPS, the 'Rationale' section should explain how it addresses the CPS, and answer any questions that the CPS poses for potential solutions.
-->

*`subject `*



## Path to Active

### Acceptance Criteria
<!-- Describes what are the acceptance criteria whereby a proposal becomes 'Active' -->
Certificates are being issued under this form by multiple DApps auditors and certification companies.
Certificates are being displayed by multiple DApps stores or aggregators which uses this format.

### Implementation Plan
<!-- A plan to meet those criteria. Or `N/A` if not applicable. -->
 - [ ] This CIP will be discussed at the Cardano Certification Working Group where multiple auditors are being represented. This will ensure that they agree on the content and are ready to issue Level 2 certificates under this format.
 - [ ] This CIP will be presented at the Cardano Fans team which aggregates this type of data so they start using this format as a basis for their certificate aggregations.
 - [ ] This CIP will be presented to the IOG Lace team which will display certificates for registered DApps. 

## Copyright
<!-- The CIP must be explicitly licensed under acceptable copyright terms. -->

[CC-BY-4.0]: https://creativecommons.org/licenses/by/4.0/legalcode
