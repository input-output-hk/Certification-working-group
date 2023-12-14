# Cardano Certification Standard

**Draft version**
**Last modification September 21th 2023**
**Authors:**

- Romain Soulat

## 1 Introduction

The Cardano Certification Standard (CCS) is a framework designed to facilitate the comparability of independent evaluations within the Cardano blockchain ecosystem. This standard establishes a comprehensive set of requirements for assessing the security features of Decentralized Applications (DApps) on the Cardano blockchain, as well as the assurance measures applied during security evaluations.

The primary objective of the evaluation process is to establish a level of confidence that the security functionalities of these DApps and the assurance measures align with the predefined requirements. Consequently, the evaluation results serve as a valuable resource for end-users seeking to gauge whether a particular DApp aligns with the requirements defined here.

The Cardano Certification Standard also serves as a guide for both DApp developers and evaluators. It offers insights and best practices for the development of DApps with robust security features and provides a structured approach for evaluating their security posture.

Flexibility is a core principle of the Cardano Certification Standard. It is designed to accommodate a diverse range of evaluation methodologies, ensuring that all essential security properties required by a DApp can be effectively assessed. However, it is essential to note that the validity of an evaluation is contingent upon the specific security properties evaluated and the methods employed. Auditors and users are advised to examine the DApp's security requirements and evaluation methodologies to assess the significance of the evaluation results.

The Cardano Certification Standard aims to address:

- The protection of assets of any user interacting with the DApp
- Ensuring the accessibility and liveness of the service provided by the DApp
- ...

Moreover, the scope of the Cardano Certification Standard could extend to security aspects beyond these categories.

Nevertheless, it is important to acknowledge that certain topics are explicitly excluded from the purview of the Cardano Certification Standard.

Among these exclusions are:
- ...

In conclusion, the Cardano Certification Standard serves as a document promoting transparency, consistency, and confidence in the security of DApps.

*RSoulat* This document draws heavily from the work of Common Criteria. I think we should take some inspiration from it for the security aspects, and, if we want to deal with purely functional aspects, add them where we see fit.

## 2 General model

### 2.1 Scope

The CCS wishes to establish the general concepts and principles of DApp security evaluation and to specify the general model of evaluation. This section provides an overview of all the parts of the CCS, it defines all the different terms, abbreviations and concepts used through the rest of the document. It establishes the core principles of the standard:

- Protection Profiles
- Security Targets
- Target of Evaluation
- Evaluation Levels

### 2.2 Terms and Definitions

*RSoulat* Note: Taken from the CC definitions
*RSoulat* Maybe we could drop the Protection Profiles from a first version and only deal with Security Target

**Adverse action**: An action performed by a Theat agent on an Asset

**Asset**: Entity that the owner of the Target of Evaluation places value on.
*RSoulat* Example of assets we could consider: Ada, Tokens, NFTs, Wallet private keys

**Attack potential**: Measure of the effort needed to exploit a vulnerability in a Targer of Evaluation (TOE)

**Attack Surface**: Set of logical interfaces to a target, which provide access to the target's assets or control.
*RSoulat* I removed "physical" and changed a bit the definition from the CC definition to better fit (I believe) what we're doing.

**Decentralized Application**: Set of software running both on the blockchain, smart contracts, and on classical servers, off-chain code, and potentially accessing third-party services.

**Developer**: Organization responsible for the development of the Target of Evaluation

**Entity**: Identifiable item that is described by a set of properties. For example: subjects, users, objects, information sessions, resources, digital assets, wallet private keys, ...

**Evaluation Level**: Well formed package of security assurance requirements representing a point on the predefined assurance scale.

**Evaluation authority**: Body operating an evaluation scheme
*RSoulat* Could be Auditors, or any "certificate provider", the difference with the CC is that the evaluation authority is **not** the certificate issuer

**Exploitable vulnerability**: Weakness in the Target of Evaluation (TOE) that can be used to violate the Security Functional Requirement (SFRs) in the Operation Environment (OE) for the TOE

**Object**: Entity in the Target of Evaluation that contains or receives information and upon which subjects perform operations.
*RSoulat* Maybe we could also augment this definition to include UTxOs? 

**Operation Environment**: Enfironment in which the Target of Evaluation (TOE) is operated, consisting of everything that is outside the TOE boundary
*RSoulat* For example, the ledger, the other contracts, the off-chain code if the TOE is only the on-chain component

**Potential vulnerability**: Suspected, but not confirmed, weakness

**Protection Profile (PP)**: Implementation-independent statement of the security needs for a Target of Evaluation (TOE) type

**Residual Vulnerability**: Weakness that cannot be exploited in the Operational Environment for the Target of Evaluation but that can be used to violate a Security Functional Requirement (SFR) by an attacker with greater Attack Potential than is anticipated in the operational environment for the TOE.

**Security Assurance Requirements**: Security requirements that refers to the conditions and processes for the development and delivery of the Target of Evaluation (TOE) and the actions required of evaluators with respect to evidence produced from these conditions and processes.

**Security Functional Requirements**: Security requirements, which contributes to fulfil the Target of Evaluation (TOE) Security Problem Definition (SPD) as defined in a specific Security Target (ST) or in a Protection Profile (PP).

**Security Objective**: Statement of an intent to counter identified threats and/or identified organization security policies and/or assumptions.
*RSoulat* Maybe overkill, maybe we could just have "counter identified threats" and not the rest. Even though I think organization security policies are a big component of security even for a DApp.

**Security Problem Definition**: Statement, which in a formal manner defines the nature and scope of the security that the Target of Evaluation (TOE) is intended to address
*RSoulat* I think this is one of the main thing we need to address

**Security Requirement**: Requirement, which is part of a Target of Evaluation (TOE) security specification as defined in a specific Security Target (ST) or in a Protection Profile (PP)

**Security Target**: Implementation-dependant statement of security requirements for a Target of Evaluation (TOE) based on a Security Problem Definition (SPD)

**Subject**: Entity in the Target of Evaluation (TOE) that performs operations on objects

**Target of Evaluation**: Set of software which is the subject of an evaluation
*RSoulat* I dropped the "hardware" and "firmware" part of the CC definition

**Vulnerability**: Weakness in the Target of Evaluation (TOE) that can be used to violate the Security Functional Requirement (SFRs) in the Operation Environment (OE) for the TOE

### 2.3 Abbreviations

**CCS**: Cardano Certification Standard

**DApp**: Decentralized Application

**OE**: Operation Environment

**PP**: Protection Profile

**SFR**: Security Functional Requirement

**SPD**: Security Problem Definition

**ST**: Security Target

**TOE**: Target of Evaluation

## 3 Overview

### 3.1 Audience

The CCS is intended for the following audiences:

- DApp users
- DApp developers
- DApp evaluators

### 3.1.1 DApp users

The CCS aims at ensuring that evaluation fulfils the needs of DApp users as this should be the fundamental purpose and justification for the evaluation process.

DApp users should be able to use the results of the evaluations to help decide whether they wish to interact with a particular DApp.

The CCS should aims at giving the DApp users implementation-independent evaluation results that can be used to compare different DApps.

### 3.1.2 DApp developers

The CCS should provide DApp developers with a set of requirements that can be used to develop DApps with robust security features. The security requirements should be known to the DApp developers before the development of the DApp starts whether their requirements come from an implementation-independent Protection Profile (PP) or from Security Requirements presented in the Security Target (ST) that they have developed themselves.

### 3.1.3 DApp evaluators

The CCS should provide DApp evaluators with a set of requirements that can be used to evaluate the security features of a DApp. This set of requirements would then help them form judgements about the conformance of the TOE, PP or ST to the requirements.

The CCS should also describe the set of actions an evaluator needs to perform to conduct an evaluation so that the evaluation results are consistent and comparable across multiple DApps audited by different evaluators.

## 3.2 Target of Evaluation

### 3.2.1 General

The CCS should be flexible enough in what is evaluated so that it can be applied to a wide range of DApps. The CCS should be able to be applied to the whole DApp or only to a the most critical parts of it.

The TOE could be a DApp, a part of a DApp, a set of full DApps, or a set of parts of DApps.

One aspect that should be considered is the dependencies with external libraries. 

The evaluation of a TOE containing only a part of a DApp should not be misrepresented as the evaluation of a whole DApp.
The evaluation of a TOE containing only a part of a DApp should be able to be used for the future evaluation of the whole DApp.

## 3.2.2 TOE boundaries

The concept of TOE boundary is fundamental to the specification of the ST.

A TOE may be a complete DApp, a part of a DApp, a set of DApps, or a set of parts of DApps. The ST needs to clearly identify the logical boundaries of the TOE.

Any parts of the overall product that are not included in the TOE are considered to be outside the scope of the evaluation.

## 3.2.3 Parametrization of a TOE

A DApp could be parametrized in many ways prior to deployment. Parts of a DApp could be created on-the-fly by the DApp itself. The TOE should clearly list the set of parameters that were considered.

An evaluation of such a TOE should clearly list the set of parameters that were considered and on which the evaluation was based on. A certificate can only refer to a version of the TOE with a parameter choice that matches one in the set considered for the evaluation.

## 3.2.4 Operational environment of the TOE

Everything outside the TOE boundary belongs the Operational Environment (OE) of the TOE. In the case of the evaluation of part of DApp, the non-TOE parts of the DApp are parts of the OE.

The ST needs to describe the assumptions on the OE so that together with the security functionalities provided by the TOE, the security objectives are met.

## 3.3 Specifying Security Requirements

### 3.3.1 Security Problem Definition

The SPD defines the security problem that is to be adressed and is presented in the ST. The SPD defines the threats that are to be countered by the TOE, the OE assumptions, and the organizational security policies.

#### Threats

The SPD describes the threats that the TOE is intended to counter.

A threat is an adverse action that can be performed by a threat agent on an asset.

## 3.4 Security Target

A ST is a document that describes:

- a specific TOE (features, life cycle, interfaces, the intended usage, ...)
- Conformance Claims (Which version of the standard, which PP, which EAL, ...)
- Security problem definition (assets, threats, organizational security policies, assumptions, ...)
- Security objectives (functional and assurance)
- Security requirements (functional and assurance)


## 3.5 Protection Profile

*RSoulat* I think we can drop the PP for a first version. It might become clearer when we have first drafts for example STs to ground the discussion and see which PP we can establish.

## 3.5 Evaluation Levels

The CCS should define a set of evaluation levels that can be used to evaluate the security features of a DApp. The evaluation levels should be defined in a way that they can be used to compare the security features of different DApps.

### 3.5.1 EAL1 - Automated testing

This level of evaluation is based on the functional testing of the TOE to determine whether the TOE meets the security requirements. The testing is performed by the developer of the TOE and the use of automated tools.

At this level, the TOE is not expected to be resistant to attack. The TOE is expected to be functionally correct and to be free of vulnerabilities that are checkable automatically.

At this level of evaluation, the analysis of the Security Target has to be left to the end-user. The quality of the Security Target cannot be addressed automatically.

### 3.5.1 EAL2 - Manual testing

This level of evaluation is based on the testing of the TOE to determine whether the TOE meets the security requirements. The testing is performed by the developer of the TOE.

A manual audit of the Security Target is performed to ensure that the Security Target is of sufficient quality. The audit should also review the quality of the verification activities performed by the developer and could also complement it to ensure that the TOE is functionally correct and without any identified vulnerabilities.

### 3.5.3 EAL3 - Formally Verified

This level of evaluation is based on the full functional verification of the TOE to determine whether it meets the security requirements.

## Example of a Security Target
