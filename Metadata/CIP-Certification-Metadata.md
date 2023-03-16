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
- **dApp** - A decentralised application that is described by the combination of metadata, certificate and a set of used scripts.
- **dApp Store** - A dApp aggregator application which follows on-chain data looking for and verifying dApp metadata claims, serving their users linked dApp metadata.


### Properties

**subject**, an UTF-8 encoded string, is a mandatory field which is an identifier of the claim subject.

**certLevel**, an integer between 1 and 3, is a mandatory field that represents the level of certification reached in a certificate.

**certificateIssuer**, a string, is a mandatory field that represents the party that has issued the certificate. It will be used with a public list of public keys to ensure that the certificate originates from a trusted certification provider. 

**reportURLs**, an array of URLs, is a mandatory field that link to the actual certification report for anyone to read. This ensures transparency in the findings, what was and was not considered in the certification process.

**reportHash**, a string, is a mandatory field that is the blake2b-256 hash of the audit file pointed by the links in **reportURLs**. 

**summaryURLs**, an array of URLs, is a mandatory field that link to the actual certification summary for anyone to read. 

**summaryHash**, a string, is a mandatory field that is the blake2b-256 hash of the summary file pointed by the links in **summaryURLs**. 

**disclaimerURLs**, an array of URLs, is a mandatory field that link to the legal disclaimer about the content of the report pointed by **reportURLs** links.

**disclaimerHash**, a string, is a mandatory field that is the blake2b-256 hash of the summary file pointed by the links in **disclaimerURLs**. 

**scriptHashes**, containing an ordered list of all scripts that make the DApp, is a mandatory field which can be used as a link to the actual DApp running on-chain.

[TODO: A non example version of the metadata]
[TO ADD: A link to off-chain metadata, with a corresponding blake2b-256 hash]
[TO ADD: A signature of the certificate]
[TO ADD: a schema version so we allow for new schemas without relying on parsers to differentiate them]

### Example
```json
{
    "subject":              "ABCDEFG1234ABCD", // DApp store needs to ensure the uniqueness of this subject 
    "certLevel":            1,
    "certificateIssuer":    "Audit House",
    "reportURLs": [
        "https://audithouse.io/certificate.pdf",
        "ipfs://bafybeiemxfal3jsgpdr4cjr3oz3evfyavhwq"
    ]
    "reportHash": "c6bb42780a9c57a54220c856c1e947539bd15eeddfcbf3c0ddd6230e53db5fdd"

    "summaryURLs": [
        "https://audithouse.io/summary.pdf",
        "ipfs://jdke788dejknfezio793029ozoekd707d609478ff65bd8501ab9e68dd98"
    ]

    "summaryHash": "c57a54220c856c1e947ddd6230e53db5fdd539bd15eec6bb42780a9ddfcbf3c0"

    "disclaimerURLs": [
        "https://audithouse.io/disclaimer.pdf",
        "ipfs://ezio5abjwjbikoz4mc3a3dla6ujknf01ab9e68dd98kd707d609478ff6"
    ]

    "disclaimerHash": "c57a54220c856c1e947ddd6230e53db5fdd539bd15eec6bb42780a9ddfcbf3c0"


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

[TO ADD: Compilation chain, how do we represent that? with versions, compilation options]
[TO ADD: Verification tools, how do we represent that? with versions, compilation options]

```json
{
    "compiler": "", // compiler + version + options, compilation options?
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

An on-chain solution is preferred as it allows for it to be checkable by any stakeholder and immutable.

Certificate are issued by certification providers that sign the certificate to prevent certificate forgeries.
This design allows for anyone to issue certificates as long as they sign it but stakeholders are then free to maintain a list of the trusted certification providers.

These certificates are self-standing and can be presented as-is by any stakeholder.

This proposal does not affect any backward compatibility of existing solution but is based on the work done for CIP72 on DApp registration and Discovery. It is also linked to CIP52 on Cardano audit best practices guidelines.

### Other designs considered
**Updates to registration entries**
This would have required DApp owner or certification providers to add certificates to every registration making it harder to maintain a shared state between all stakeholders. The chosen design requires to follow the chain to discover the certificates which should be expected from stakeholders.


## Path to Active

### Acceptance Criteria

Certificates are being issued under this form by multiple DApps auditors and certification companies.

Certificates are being displayed by multiple DApps stores or aggregators which uses this format.

### Implementation Plan
 - [ ] This CIP will be discussed and agreed by the Cardano Certification Working Group where multiple auditors are being represented. This will ensure that certification issuer have agreed on the content and are ready to issue certificates under this format.

 - [ ] This CIP will be presented to the IOG Lace team and Cardano Fans team which will display certificates for DApps. This is to ensure that the format contains all the necessary information for a DApp store or an aggregator to correctly link and display a certificate from the on-chain and off-chain metadata.

## Copyright
<!-- The CIP must be explicitly licensed under acceptable copyright terms. -->

[CC-BY-4.0]: https://creativecommons.org/licenses/by/4.0/legalcode
