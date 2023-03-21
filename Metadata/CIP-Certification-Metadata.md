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


### Definitions
- **anchor** - A hash written on-chain that can be used to verify the integrity (by way of a cryptographic hash) of the data that is found off-chain.
- **dApp** - A decentralised application that is described by the combination of metadata, certificate and a set of used scripts.
- **dApp Store** - A dApp aggregator application which follows on-chain data looking for and verifying dApp metadata claims, serving their users linked dApp metadata.
- **Certification providers** - A company that issues certification certificates on-chain.

### Certification providers
Certification providers will broadcast on-chain certificates that will represent th level of certification reached and present evidence of the work done.
Certification providers will sign the certificate to attest that they have done the work and prevent certificate forgeries.

### Suggested validations
- `integrity`: The DApp's metadata off-chain shall match the metadata **anchored** on-chain.
- `trust`: The DApp's certification metadata shall be signed by a trusted certfication provider. This means a list of public keys of certification providers needs to be known. It will then be up to the DApp store to decide which certification providers are really trusted and publish a list of their own certification provider.

### On-chain DApp Certification Certificate
```json
{
    "subject": "d684512ccb313191dd08563fd8d737312f7f104a70d9c72018f6b0621ea738c5b8213c8365b980f2d8c48d5fbb2ec3ce642725a20351dbff9861ce9695ac5db8", 
    "rootHash": "f08ccc1ee08d034d8317d1d84cab76d3cac48a8466ca9e54a291bb998c49a1732e93280bf04a11293c73195affe4fcaa41f7b27c067396f97f701dd96f72665e",
    "metadata": [
        "https://audithouse.io/certification/report.pdf",
        "https://greatdapp.com/certification/AuditHouse_report.pdf"
    ]

    "schema_version": "1.0",
    "type": {
        "action": "CERTIFY",
        "certificationLevel": "1",
        "certificateIssuer": "Audit House LLC"
    },

    "signature": {
        "r": "5114674f1ce8a2615f2b15138944e5c58511804d72a96260ce8c587e7220daa90b9e65b450ff49563744d7633b43a78b8dc6ec3e3397b50080",
        "s": "a15f06ce8005ad817a1681a4e96ee6b4831679ef448d7c283b188ed64d399d6bac420fadf33964b2f2e0f2d1abd401e8eb09ab29e3ff280600",
        "algo": "Ed25519−EdDSA",
        "pub": "b7a3c12dc0c8c748ab07525b701122b88bd78f600c76342d27f25e5f92444cde"// Audit House LLC public key
    }


```

### Properties

`subject`: Identifier of the claim subject (i.e dApp). A UTF-8 encoded string. 

`type`: The type of the claim. This is a JSON object that contains the following properties:

- `action`: The action that the certificate is asserting. It can take the following values:
    - `CERTIFY`: The certificate is asserting that the dApp is being registered for the first time.
        [IDEA: Revoke? Update?]
    - `certificationLevel`: The certification level, between 1 and 3, in accordance with the Certification Working Group standards for certification level.
    - `certificationIssuer`: The name of the certification issuer.



`rootHash`: The hash of the metadata entire tree object. This hash is used by clients to verify the integrity of the metadata tree object. When reading a metadata tree object, the client should calculate the hash of the object and compare it with the rootHash property. If the two hashes don't match, the client should discard the object. The metadata tree object is a JSON object that contains the dApp's metadata. The metadata tree object is described in the next section.

This hash is calculated by taking the entire metadata tree object, ordering the keys in the object alphanumerically, and then hashing the resulting JSON string using the **blake2b-256** hashing algorithm. The hash is encoded as a hex string.

`metadata`: An array of links to the dApp's metadata. The metadata is a JSON object that contains the dApp's metadata in accordance with [CIP 26](https://cips.cardano.org/cips/cip26/)

`signature`: The signature of the certificate. The signature is done over the blake2b-256 hash of the certificate. The client should use the public key to verify the signature of the certificate.


### Certificate JSON Schema
[TODO: Fully understand the spec for JSON Schema, this is currently taken from CIP72 with some rewritting to fit Certification but I am not fully sure if everything is correctly filled]
```json
{
    "$schema": "https://json-schema.org/draft/2019-09/schema", // [TODO: Not sure about this one]
    "$id": "YYY", // [TODO: Not sure about this one]
    "title": "Certification", // [TODO: Not sure about this one]
    "type": "object", // [TODO: Not sure about this one]
    "properties": {
      "subject": {
        "type": "string",
        "description": "Can be anything. Subject of the certification.",
      },
      "type": {
        "type": "object",
        "description": "Describes the certification certificate.", 
        "properties": {
          "action": {
            "type": "string",
            "description": "Describes the action this certification certificate is claiming. For the moment, only 'CERTIFY' is possible but we want to leave the possibility for new actions in the future"
          },
          "certificatioNlevel": {
            "type": "integer",
            "description": "Integer between 1 and 3 to describe the level of certification this certificate refers to"
          },
          "certificateIssuer": {
            "type": "string",
            "description": "Certification provider name"
          }
        }
      },  
      "rootHash": {
        "type": "string",
        "description": "blake2b hash of the metadata describing the dApp"
      },
      "signature": {
        "description": "The signature of the certification certificate by the certification provider",
        "type": "object",
        "properties": {
            "r": {
                "type": "string",
                "description": "hex representation of the R component of the signature"
            },
            "s": {
                "type": "string",
                "description": "hex representation of the S component of the signature"
            },
              
        },
        "required": ["r", "s", "algo", "pub"]
      }
    },
    "required": ["subject", "rootHash","type", "signature"]
}
```


### Metadata Label
When submitting the transaction metadata pick the following value for `transaction_metadatum_label`:


- `1304`: DApp Certification
[TODO: Pick a number and register it in accordance to [CIP10](https://cips.cardano.org/cips/cip10/)]

### Off-chain Metadata Format
The Dapp Certification certificate is complemented by off-chain metadata that can be fetched from off-chain metadata servers.

### Properties


**certificateIssuer**, a string, is a mandatory field that represents the party that has issued the certificate. It will be used with a public list of public keys to ensure that the certificate originates from a trusted certification provider.

**report**, an object that contains:
- **reportURLs**, an array of URLs, is a field where each link points to the same actual certification report for anyone to read. This ensures transparency in the findings, what was and was not considered in the certification process..

- **reportHash**, a string, is a field that is the blake2b-256 hash of the report pointed by the links in **reportURLs**. 

**summary**, an object that contains:
- **summaryURLs**, an array of URLs, is a mandatory field that link to the actual certification summary for anyone to read. 

- **summaryHash**, a string, is a mandatory field that is the blake2b-256 hash of the summary file pointed by the links in **summaryURLs**. 

**disclaimer**, an object that contains:
- **disclaimerURLs**, an array of URLs, is a mandatory field that link to the legal disclaimer about the content of the report pointed by **reportURLs** links.

- **disclaimerHash**, a string, is a mandatory field that is the blake2b-256 hash of the summary file pointed by the links in **disclaimerURLs**. 

**script** an array of objects that represents the whole DApp's on-chain script. Each object is comprised of:
- **fullScriptHash**, a string, is the prefix and script hash or script hash+staking key
- **scriptHash**, a string, is the script hash or script hash+staking key
- **contractAddress**, a string, the script address


The off-chain metadata should follow the following schema:

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",  // [TODO: Not sure about this one]
  
  "type": "object",
  "properties": {
    "subject": {
      "type": "string"
    },
    "schemeVersion": {
      "type": "string"
    },
    "certificationLevel": {
      "type": "integer"
    },
    "certificateIssuer": {
      "type": "object",
      "properties": {
        "name": {
           "type": "string"
        },
        "email": {
          "type": "string"
        },
        "social": {
          "type": "object",
          "properties": {
            "twitter": {
              "type": "string"
            },
            "github": {
              "type": "string"
            },
            "website": {
              "type": "string"
            }
          },
          "required": [
              "website"
          ]
        },
      },
      "required": [
          "name",
          "email",
          "social"
      ]
    },
    "report": {
      "type": "object",
      "properties": {
        "reportURLs": {
          "type": "array",
          "items": [
              "type": "string"
          ]
        },
        "reportHash": {
          "type": "string"
        }
      },
      "required": [
          "reportURLs",
          "reportHash"
      ]
    }
    "summary": {
      "type": "object",
      "properties": {
        "summaryURLs": {
          "type": "array",
          "items": [
              "type": "string"
          ]
        },
        "summaryHash": {
          "type": "string"
        }
      },
      "required": [
          "summaryURLs",
          "summaryHash"
      ]
    }
    "disclaimer": {
      "type": "object",
      "properties": {
        "disclaimerURLs": {
          "type": "array",
          "items": [
              "type": "string"
          ]
        },
        "disclaimerHash": {
          "type": "string"
        }
      },
      "required": [
          "disclaimerURLs",
          "disclaimerHash"
      ]
    }
    "scripts": {
      "type": "array",
      "items": [
        {
            "type": "object",
            "properties": {
                "era": {
                  "type": "string"
                },
                "compiler": {
                  "type": "string"
                },
                "fullScriptHash": {
                  "type": "string"
                },
                "scriptHash": {
                  "type": "string"
                },
                "contractAddress": {
                  "type": "string"
                }
            },
            "required": [
                "fullScriptHash",
                "scriptHash",
                "contractAddress"
              ]
        }
      ]
    }
  },

  "required": [
    "subject",
    "schemeVersion",
    "certificationLevel",
    "certificateIssuer",
    "report",
    "summary",
    "disclaimer",
    "scripts"
  ]
}
```

### Example

```json
{
  "subject": "d684512ccb313191dd08563fd8d737312f7f104a70d9c72018f6b0621ea738c5b8213c8365b980f2d8c48d5fbb2ec3ce642725a20351dbff9861ce9695ac5db8",
  "schemeVersion": "1.0.0",
  "certificationLevel": 1,
  "certificateIssuer": {
    "name": "Audit House LLC",
    "email": "contact@audithouse.com"
    "link": "https://audithouse.com",
    "social": {
        "twitter": "twiterHandle",
        "github": "githubHandle",
        "website": "https://website"
  },
  "report": {
    "reportURLs": [
        "https://audithouse.io/certificate.pdf",
        "ipfs://bafybeiemxfal3jsgpdr4cjr3oz3evfyavhwq"
        ],
    "reportHash": "c6bb42780a9c57a54220c856c1e947539bd15eeddfcbf3c0ddd6230e53db5fdd"
  },
  "summary": {
    "summaryURLs": [
        "https://audithouse.io/summary.pdf",
        "ipfs://jdke788dejknfezio793029ozoekd707d609478ff65bd8501ab9e68dd98"
    ],
    "summaryHash": "c57a54220c856c1e947ddd6230e53db5fdd539bd15eec6bb42780a9ddfcbf3c0"
  },
  "disclaimer": {
    "disclaimerURLs": [
        "https://audithouse.io/disclaimer.pdf",
        "ipfs://ezio5abjwjbikoz4mc3a3dla6ujknf01ab9e68dd98kd707d609478ff6"
    ],
    "disclaimerHash": "c57a54220c856c1e947ddd6230e53db5fdd539bd15eec6bb42780a9ddfcbf3c0"
  }
  "scripts": [
        {
          "era": "basho",
          "compiler": "plutusTX"
          "fullScriptHash": "711dcb4e80d7cd0ed384da5375661cb1e074e7feebd73eea236cd68192",
          "scriptHash": "1dcb4e80d7cd0ed384da5375661cb1e074e7feebd73eea236cd68192",
          "contractAddress": "addr1wywukn5q6lxsa5uymffh2esuk8s8fel7a0tna63rdntgrysv0f3ms"
        },
        {
          "era": "basho",
          "compiler": "plutusTX"
          "fullScriptHash": "384da5375661cb1e07713eea236cd681921dcb4e80d7cd0ed4e7feebd7",
          "scriptHash": "6cd68191dcb4e80d7c5661cb1e074e7feebd73eea232d0ed384da537",
          "contractAddress": "addr1wywukn5q6lrdntgrysv0f7a0tna63ymffh23ms5uxsaesuk8s8fel"
        }
  ]
}
```

[TO ADD: Compilation chain, how do we represent that? with versions, compilation options]
[TO ADD: Verification tools, how do we represent that? with versions, compilation options]

```json
{
    "compiler": "", // compiler + version + options, compilation options?
    "certificationArtifacts": ["", ""] // links to all the certification artifacts test runs, formal proof objects, certification compilation proof object etc.
    "verificationTools": "",
    "repository": "",
    "scriptParameters": "", 
}
```

The metadata should be discoverable by all certification stakeholders, including end-users, DApp developers, and ecosystem components, such as light wallets and DApp stores. Information should be indexable by certification provider, DApp developer, DApp and DApp version.

It should be possible for there to be multiple versions of metadata published by the same certification provider for the same version of a DApp, particularly when a (minor) update of the evidence is necessary. In such a case it should be possible to identify the most recent version of the report for that DApp version. It will also be the case that the same DApp may have certification metadata provided by multiple different certification providers.

It should be possible for wallets to identify to users the certification status of a DApp when they are signing a transaction that is being submitted to a deployed DApp.

### Custom fields
Certification providers should be free to add additional fields to fit some additional needs.

## Rationale: how does this CIP achieve its goals?

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
