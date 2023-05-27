---
CIP: ???
Title: Cardano Threat Intelligence
Category: ???
Status: Proposed
Authors: ???
Implementors: []
Discussions:
    - https://github.com/input-output-hk/Certification-working-group/pull/21
    - https://github.com/input-output-hk/Certification-working-group/pull/22
Created: ????-??-??
License: CC-BY-4.0
---

## Abstract

Cardano Threat Intelligence (CTI) is a crucial practice that involves gathering and analyzing information to proactively identify and mitigate potential threats to the Cardano blockchain platform. CTI utilizes a categorization system in a community-led repository, organizing vulnerabilities and weaknesses based on Cardano's different layers (on-chain, off-chain, network, and miscellaneous). Each issue is assigned a reference number by the CTI for easy identification.

Threat intelligence in Cardano is gathered through diverse methods, including monitoring online communities, analyzing network traffic, collaborating with experts, and conducting threat modeling exercises. The CTI Watchdogs, a group of cybersecurity, blockchain, and threat analysis experts, play a vital role in managing CTI and maintaining the security and integrity of the Cardano ecosystem.

The benefits of Cardano Threat Intelligence are significant, enabling early threat identification, enhanced network security, mitigation of financial and reputational risks, and staying ahead of emerging threats and vulnerabilities.

Implementing a Cardano Threat Intelligence framework is essential to safeguard the ecosystem. By leveraging threat intelligence practices and maintaining a well-organized repository, the Cardano community can proactively address vulnerabilities and ensure the ongoing security and trustworthiness of the network.

## Motivation: why is this CIP necessary?

This CIP addresses the growing importance of security within the Cardano blockchain ecosystem. As Cardano gains popularity, it becomes a target for malicious actors seeking to exploit vulnerabilities and compromise the platform's integrity. The primary goal of this CIP is to establish a dedicated framework for Cardano Threat Intelligence (CTI) that proactively identifies, analyzes, and mitigates potential threats and vulnerabilities. By implementing a structured approach, the Cardano community can stay ahead of evolving security risks and ensure the continued resilience and trustworthiness of the network.

CTI plays a crucial role in enhancing the overall security posture of Cardano. It enables early detection and assessment of potential threats, facilitating prompt actions to prevent or mitigate their impact. CTI also encourages collaboration among security researchers, experts, and stakeholders, fostering a collective effort to maintain the platform's security. By exchanging information and insights, the community stays informed about emerging threats and evolving attack techniques.

Furthermore, CTI includes post-mortem analysis to properly document exploited vulnerabilities. This analysis provides valuable insights into the root causes, impact, and remediation strategies associated with security incidents. It contributes to continuous improvement in security practices and strengthens the overall robustness of the Cardano ecosystem.

Through the formalization of the Cardano Threat Intelligence framework in this CIP, we aim to create a standardized and community-driven approach to threat intelligence. This empowers the community to actively contribute to threat identification, analysis, and mitigation, establishing a proactive and robust security ecosystem for Cardano's sustained growth and success.

### Use-cases and Stakeholders

The Cardano Threat Intelligence (CTI) framework has several key use-cases and stakeholders involved in its implementation and utilization. These use-cases demonstrate the breadth of applications for CTI and the diverse range of stakeholders who benefit from its adoption.

**Security and Risk Management**: CTI serves as a valuable tool for security and risk management within the Cardano ecosystem. It enables the identification, assessment, and mitigation of potential threats, vulnerabilities, and weaknesses. Security teams, risk analysts, and auditors can leverage CTI to enhance their understanding of security risks, make informed decisions, and develop strategies to protect the Cardano network.

**Cardano Development Teams**: CTI plays a crucial role in supporting Cardano's development teams. By providing valuable intelligence on vulnerabilities and weaknesses, CTI helps inform the development process and encourages the integration of security measures from the early stages. Development teams can use CTI to prioritize security enhancements, address identified issues, and ensure the overall integrity and resilience of Cardano's codebase.

**Cardano Community**: The Cardano Community also benefits indirectly through improved development processes and enhanced security of the DApps they interact with. By leveraging CTI, the community gains access to up-to-date information about potential threats and vulnerabilities. This allows community members to contribute by reporting new findings, sharing insights, and collaborating with the CTI Watchdogs. By actively participating in CTI, the Cardano community plays a crucial role in maintaining the overall security of the network. This fosters a sense of shared responsibility among stakeholders and strengthens the security of the DApps utilized by the community.

**Exchanges and Wallet Providers**: CTI is of significant importance to exchanges and wallet providers that support Cardano. By integrating CTI into their security practices, these stakeholders can enhance their risk assessment processes, strengthen their defenses against potential threats, and safeguard user assets and sensitive data.

**Blockchain Security Researchers and Analysts**: CTI provides a valuable resource for blockchain security researchers and analysts. They can leverage the CTI repository to study trends, identify new attack vectors, and contribute their expertise to the ongoing improvement of Cardano's security posture. CTI fosters collaboration and knowledge sharing among security professionals, resulting in a more resilient and robust blockchain ecosystem.

The use-cases and stakeholders mentioned above demonstrate the diverse range of individuals and entities that benefit from the adoption of CTI within the Cardano ecosystem. By fostering collaboration, knowledge sharing, and proactive security practices, CTI contributes to the overall trust, security, and long-term success of the Cardano blockchain platform.

## Specification

### Definitions

**Vulnerability**:  In the context of this CIP, a vulnerability refers to any specific flaw or weakness in the design, implementation, or configuration of the Cardano blockchain platform or any associated decentralized applications (DApps) within the Cardano ecosystem. It encompasses potential security risks that, if successfully exploited, may lead to unauthorized access, data breaches, financial loss, or service disruptions. Vulnerabilities require immediate attention and remediation to prevent potential exploitation and protect the security and integrity of the Cardano ecosystem.

**Weakness**: A weakness, in the context of this CIP, refers to an inherent limitation, deficiency, or susceptibility within the Cardano ecosystem that may impact its security or performance. Unlike vulnerabilities, weaknesses may not present an immediate or exploitable risk. However, they still require attention to prevent future vulnerabilities from emerging or to optimize the overall security and performance of the Cardano ecosystem.

**Cardano Threat Intelligence (CTI)**: Cardano Threat Intelligence is the practice of gathering, analyzing, and disseminating information about potential threats, vulnerabilities, and weaknesses within the Cardano blockchain platform. CTI aims to provide proactive insights and mitigation strategies to enhance the security and resilience of the network.

**CTI Repository**: The CTI Repository is a community-led resource that serves as the collection of information related to Cardano Threat Intelligence. It contains categorized vulnerabilities, weaknesses, and associated data, facilitating knowledge sharing, collaboration, and proactive security measures within the Cardano community.

**CTI Identifier**: In the context of Cardano Threat Intelligence (CTI), a CTI Identifier refers to a unique alphanumeric code assigned to each vulnerability or weakness within the CTI repository. The CTI Identifier follows a standardized numbering scheme, enabling easy identification, categorization, and reference of specific vulnerabilities and weaknesses within the Cardano ecosystem.

**CTI Template**: In the context of Cardano Threat Intelligence (CTI), a CTI template refers to a standardized format or structure used to document and present information about vulnerabilities and weaknesses identified within the Cardano blockchain platform. The CTI template serves as a consistent framework for capturing relevant details and providing a comprehensive overview of each vulnerability or weakness.

### CTI Repository

The CTI repository serves as a location for storing and managing the collection of vulnerabilities and weaknesses discovered within the Cardano ecosystem. It provides a structured and organized approach to categorize and document these security findings, ensuring that they are easily accessible and retrievable by relevant stakeholders.

<!---
???? = IOG (Input Output Global) or Cardano Foundation GitHub account
-->
The CTI repository will be hosted under the ???? GitHub account. The location of the CTI repository within the ???? GitHub account will provide a hub for security researchers, developers, and other stakeholders to contribute to the identification, analysis, and resolution of vulnerabilities and weaknesses within the Cardano ecosystem. It allows for efficient collaboration, version control, and transparency in the handling of security-related issues.

### CTI Identifier

#### Categorization System and Numbering Scheme

The Cardano Threat Intelligence (CTI) repository follows a specific format and numbering system to categorize vulnerabilities and weaknesses based on the different layers of Cardano's blockchain. This system provides a comprehensive and standardized approach to organize and reference vulnerabilities within the Cardano ecosystem.

##### Properties

The CTI numbering system is structured as follows:

Format: CTI-YYYY-AAA-TT-N

**CTI**: Acronym for "Cardano Threat Intelligence"
**YYYY**: A four-digit year representing the discovery year of the vulnerability/weakness
**AAA**: A three-letter identifier denoting the protocol or network associated with the vulnerability/weakness (e.g., ADA for Cardano main-chain, MKD for Milkomeda side-chain, etc.)
**TT**: A two-digit combination comprising high-level category and subcategory codes that define the type of vulnerability/weakness. The initial set of categories and subcategories have been established, including on-chain, off-chain, network, and miscellaneous vulnerabilities and weaknesses. However, it is important to note that these subcategories are not fixed and can be subject to modification based on discussions among the CTI Watchdogs and other stakeholders. The CTI Watchdogs, in collaboration with the Cardano community, will evaluate the needs and requirements and make necessary adjustments to the subcategories to ensure effective categorization and organization of vulnerabilities and weaknesses.

**N**: A natural number assigned to the vulnerability/weakness within its respective category and subcategory

##### Examples

  10: On-chain vulnerabilities
    01: Smart contract vulnerabilities
    02: Consensus mechanism vulnerabilities
    ...
  20: Off-chain vulnerabilities
    01: Oracle-related vulnerabilities
    02: Sidechain-related vulnerabilities
    ...
  30: Network vulnerabilities
    01: DDoS attack vulnerabilities
    02: Peer-to-peer network attack vulnerabilities
    ...
  40: Miscellaneous vulnerabilities
  50: On-chain weaknesses
    01: Smart contract weaknesses
    02: Consensus mechanism weaknesses
    ...
  60: Off-chain weaknesses
    01: Oracle-related weaknesses
    02: Sidechain-related weaknesses
    ...
  70: Network weaknesses
    01: DDoS attack weaknesses
    02: Peer-to-peer network attack weaknesses
  ...
  80: Miscellaneous weaknesses

CTI-2021-ADA-11-1: Reentrancy vulnerability in PlutusTx smart contract
CTI-2022-MKD-61-34: Incorrect handling of error conditions in Milkomeda oracle
CTI-2023-ADA-31-11: DDoS attack on Cardano network
CTI-2024-MKD-33-100: Routing attack on Milkomeda

### CTI Template

The CTI template serves as a standardized format for documenting and sharing information about vulnerabilities and weaknesses within the Cardano ecosystem. It provides a structured framework to describe the details of each vulnerability/weakness, ensuring consistency and clarity in communication among stakeholders.

In the following sections, each component of the CTI template will be described in detail, providing comprehensive information about the vulnerability/weakness. These sections include:

#### CTI-YYYY-AAA-TT-N: The Vulnerability/Weakness Title

This section provides descriptive information about each component of the CTI template format used for documenting vulnerabilities and weaknesses within the Cardano Threat Intelligence (CTI) repository. It outlines the key sections included in the template and their respective purposes.

#### Author

The Author section includes information about the person or team responsible for identifying the vulnerability/weakness. It specifies their names, roles, organization or company affiliation, and contact information. Additionally, any relevant certifications or qualifications held by the individuals or team may be mentioned.

#### Summary

The Summary section provides a brief overview of the vulnerability/weakness finding. It includes a descriptive title that accurately summarizes the nature of the identified vulnerability/weakness.

#### Description

The Description section offers a detailed account of the vulnerability/weakness, encompassing the affected system or software and the method through which it was discovered. It may include relevant background information that aids in stakeholders' understanding of the problem. The impact of the vulnerability/weakness is also described in clear and concise language.

#### Risk Assessment

- **Likelihood:** The probability of the vulnerability/weakness being exploited or an attack being successful. The Likelihood levels can be defined as follows:
  - **Low:** The likelihood of a vulnerability/weakness being exploited is considered low, either because the vulnerability/weakness is difficult to find or because it would require a sophisticated attacker to exploit it.
  - **Medium:** The likelihood of a vulnerability/weakness being exploited is considered medium, meaning that an attacker with some level of skill could potentially exploit it.
  - **High:** The likelihood of a vulnerability/weakness being exploited is considered high, meaning that an attacker with minimal skill could potentially exploit it.

- **Difficulty:** The difficulty of exploiting the vulnerability/weakness, including the level of skill and resources required by an attacker to carry out an attack.The Difficulty  levels can be defined as follows:
  - **Low:** The difficulty of exploiting a vulnerability/weakness is considered low, meaning that the attacker could easily exploit the vulnerability/weakness with minimal resources.
  - **Medium:** The difficulty of exploiting a vulnerability/weakness is considered medium, meaning that the attacker would require some level of expertise or resources to exploit it.
  - **High:** The difficulty of exploiting a vulnerability/weakness is considered high, meaning that the attacker would require significant expertise or resources to exploit it.

Combining likelihood and difficulty factors can help to determine the overall risk level of a vulnerability/weakness. For example, a vulnerability/weakness with a high likelihood and low difficulty would be considered a high-risk vulnerability/weakness, as it is both likely to be exploited and relatively easy to do so. On the other hand, a vulnerability/weakness with a low likelihood and high difficulty would be considered a lower-risk vulnerability/weakness, as it is less likely to be exploited and would require significant resources and expertise to do so.

- **Impact:** The potential impact of the vulnerability/weakness on the system, organization, and users, ranging from Low to High.The impact levels can be defined as follows:
  - **Low:** Vulnerabilities/Weaknesses that have minimal impact on system confidentiality, integrity, or availability.
  - **Medium:** Vulnerabilities/Weaknesses that have moderate impact on system confidentiality, integrity, or availability.
  - **High:** Vulnerabilities/Weaknesses that have significant impact on system confidentiality, integrity, or availability.

As part of the risk assessment, it is important to describe the potential impact of the vulnerability or weakness on the organization, as well as any potential legal or regulatory consequences.

- **Severity:** This assigns a level of severity to the vulnerability or weakness based on the risk assessment. The severity levels can range from High to Informational. The severity levels can be defined as follows:
  - **High:** Vulnerabilities/Weaknesses that can be easily exploited with a high impact.
  - **Medium:** Vulnerabilities/Weaknesses that can be exploited with some effort or have moderate impact.
  - **Low:** Vulnerabilities/Weaknesses that require significant effort to exploit or have low impact.
  - **Informational:** Vulnerabilities/Weaknesses that do not pose a significant risk by themselves but may provide useful information for attackers or reveal deficiencies in the security posture of the system.

Note that the severity level should be determined based on the combined assessment of likelihood/difficulty and impact.

#### Steps to Reproduce

The Steps to Reproduce section provides a detailed guide on how to replicate the vulnerability/weakness. It includes step-by-step instructions, relevant system environment information, and tools and tests utilized during the reproduction process.

#### Technical Details

The Technical Details section encompasses additional technical information pertaining to the vulnerability/weakness. This may include details about:

- Tools used
- Methodology (methods used to identify the vulnerability/weakness)
- Affected software versions
- Smart contracts that contain vulnerable code.
- Affected and impacted system configurations
- blockchain networks utilizing smart contracts.
- Examples of vulnerable code snippets.

The section also highlights other related vulnerabilities or weaknesses, including CVE, CWE, buffer overflow, SQL injection, and any other relevant types. Moreover, it provides information about the attack vector utilized to exploit the vulnerability/weakness. The technical language used in this section is aimed at ensuring stakeholders' understanding while maintaining specificity.

#### Mitigation & Remediation Steps

The Mitigation & Remediation Steps section outlines recommended actions to address and fix the vulnerability/weakness. It includes patches, software updates, system configuration changes, coding best practices, and estimated timeframes, resources, and potential implementation challenges. Workarounds to mitigate the consequences of the vulnerability/weakness while the fix is being implemented may also be suggested.

#### References

The References section lists relevant sources and references consulted during the vulnerability/weakness assessment. These may include vendor advisories, known vulnerability/weakness databases, industry-standard security guidelines, and best practices.

#### Tags

The Tags section allows for the inclusion of relevant keywords or labels that aid in categorizing and classifying the vulnerability or weakness described in the CTI template. These tags serve as additional metadata, helping to search and filter vulnerabilities or weaknesses based on specific criteria. They improve information discoverability and accessibility, ensuring that relevant vulnerabilities or weaknesses can be identified efficiently. Tags can include various aspects related to the vulnerability, such as related technologies, concepts, affected components, or potential impact. CTI watchdogs will establish conventions or agreed-upon keywords for adding tags, which should be concise, descriptive, and representative of the key attributes or characteristics of the vulnerability or weakness.

## Rationale: how does this CIP achieve its goals?

### CTI Watchdogs

The CTI Watchdogs are a group of experts responsible for managing Cardano Threat Intelligence. They possess specialized knowledge in cybersecurity, blockchain technology, threat analysis, and vulnerability management. The CTI Watchdogs play a crucial role in monitoring, analyzing, and addressing potential threats, vulnerabilities, and weaknesses in the Cardano ecosystem.

#### Responsibilities

The primary responsibilities of the CTI Watchdogs include:

**Collecting and Curating Threat Intelligence**: The team actively gathers and collects threat intelligence from various sources, such as security researchers, community reports, vulnerability databases, and external collaborations. They curate and evaluate the gathered information to ensure its relevance, accuracy, and applicability to the Cardano ecosystem.

**Analyzing and Assessing Threats**: The team conducts in-depth analysis and assessment of identified threats, vulnerabilities, and weaknesses within the Cardano network. They evaluate the potential impact and likelihood of each threat and prioritize them based on their severity and risk level.

**Maintaining the CTI List**: The CTI Watchdogs is responsible for maintaining an up-to-date CTI list that documents known vulnerabilities, weaknesses, and threats specific to Cardano. They categorize and classify the CTI list based on different layers and components of the Cardano blockchain, making it easier for the community to navigate and understand the potential risks.

**Communication and Collaboration**: The team fosters open communication and collaboration with the Cardano community, security researchers, auditors, and other relevant stakeholders. They actively engage in discussions, share updates on threat intelligence findings, and provide recommendations for mitigating identified risks. They also work closely with the Cardano development teams to ensure that vulnerabilities are promptly addressed and appropriate security measures are implemented.

**Proactive Mitigation**: The CTI Watchdogs takes a proactive approach to risk mitigation. They contribute to the development and implementation of security best practices, recommend security enhancements, and support the integration of threat intelligence findings into Cardano's development and maintenance processes.

#### Selection of CTI Watchdogs Members

The selection process for CTI Watchdogs members aims to ensure a diverse and capable team that possesses the necessary expertise and dedication to effectively manage Cardano Threat Intelligence. Transparency, community involvement, and rigorous evaluation are essential elements in forming a highly skilled and trusted group of CTI Watchdogs who can contribute to maintaining the security and integrity of the Cardano network.

The selection of CTI Watchdogs members follow a rigorous and transparent approach that includes the following steps:

**Establishment of Criteria**: The CTI Watchdogs, in collaboration with relevant stakeholders, defines the criteria and qualifications required for CTI Watchdogs members. This may include specific technical skills, experience in vulnerability assessment and analysis, familiarity with Cardano's ecosystem and different smart contract programming languages, and a track record of contributing to the security of blockchain platforms.

**Application and Nomination**: Interested individuals can submit applications or nominations for consideration as CTI Watchdogs members. This will be done through CTI Watchdogs Discord server. The application/nomination process allows individuals to showcase their qualifications, experience, and commitment to contributing to Cardano's security.

**Review and Evaluation**: CTI Watchdogs committee reviews the applications/nominations. They assess the candidates based on the established criteria, carefully evaluating their qualifications, experience, and potential contributions to CTI.

**Interview and Selection**: Shortlisted candidates may undergo an interview process, which provides an opportunity for the committee to assess their knowledge, skills, and suitability for the CTI Watchdogs role. The interviews can include technical discussions, scenario-based assessments, and an exploration of the candidates' understanding of Cardano's security challenges.

**Community Engagement**: To ensure a transparent and community-driven process, the final selection of CTI Watchdogs members may involve gathering input and feedback from the Cardano community. This will be done through CTI Watchdogs dedicated Discord server and tweeter account. The community's perspectives and insights are valuable in identifying individuals who can effectively represent and serve the community's interests.

**Appointment and Ongoing Evaluation**: Based on the evaluations, interviews, and community feedback, the selected CTI Watchdogs members are appointed to their roles. Regular evaluation and performance assessments can be conducted to ensure their continued effectiveness and alignment with the goals of the CTI framework.

#### Removal from CTI Watchdogs

To ensure the effectiveness and integrity of the CTI Watchdogs within the Cardano Threat Intelligence (CTI) framework, it is important to have a process in place for removing individuals or organizations under certain circumstances. The process will follow the steps outlined below:

**Assessment and Identification**: The need for removing a member from the CTI Watchdogs may arise due to various reasons, such as ceasing activity, failure to meet standards, or a member leaving the organization they represent. The first step is to assess the situation and identify the specific circumstances that warrant the removal.

**Review and Evaluation**: Once the need for removal is identified, a thorough review and evaluation will be conducted. This may involve examining the individual or organization's contributions, adherence to guidelines, responsiveness, and overall effectiveness in fulfilling their CTI Watchdogs responsibilities. It is important to gather sufficient evidence and consider multiple perspectives during this evaluation process.

**Decision-Making**: Based on the review and evaluation, a decision will be made regarding the removal. This decision may involve considering factors such as the severity and frequency of the issues observed, the impact on the CTI Watchdogs' effectiveness, and the overall goals and standards of the CTI framework. The decision will be fair, transparent, and consistent with the established CTI Watchdogs governance processes.

**Communication**: Once the decision to remove a member from the CTI Watchdogs is made, clear and transparent communication is essential. The member or organization in question will be informed of the decision, along with the reasons and any specific feedback or concerns identified during the evaluation process. It is important to maintain professionalism and respect during this communication to minimize potential conflicts or misunderstandings.

**Transition and Continuity**: If a member is being removed due to leaving the organization they represent, a plan will be in place to ensure a smooth transition. This may involve identifying a replacement from the same organization or initiating a selection process to fill the vacant position. The transition will be managed effectively to avoid disruptions to the CTI Watchdogs' activities and maintain continuity in the responsibilities.

**Documentation and Learning**: It is crucial to document the entire process of removing a member from the CTI Watchdogs. This documentation will include the rationale, decision, and any relevant details regarding the evaluation and communication. It serves as a reference for future actions and helps maintain transparency and accountability within the CTI framework. Additionally, it provides an opportunity for learning and improvement in the CTI Watchdogs' selection and evaluation processes.

### CTI Disclosure

By adhering to cybersecurity disclosure laws and following a well-defined process, the CTI Watchdogs aim to ensure a transparent, responsible, and low-risk disclosure process for vulnerabilities and weaknesses within the Cardano ecosystem. This approach, utilizing the CTI template format and the assigned CTI identifier, fosters trust, collaboration, and effective risk management, ultimately enhancing the overall security and resilience of the Cardano blockchain platform.

#### CTI Disclosure Process

The CTI Watchdogs are committed to ensuring a transparent and responsible disclosure process for vulnerabilities and weaknesses within the Cardano Threat Intelligence (CTI) framework. The CTI Disclosure process follows cybersecurity disclosure laws and best practices to minimize risks and protect the interests of the Cardano ecosystem and its stakeholders.

The CTI Disclosure process can be outlined in the following steps:

**Vulnerability/Weakness Discovery**: When a vulnerability or weakness is discovered within the Cardano ecosystem, it should be reported to the CTI Watchdogs. The discovery can come from various sources, including internal security audits, external researchers, community members, or third-party assessments.

**Initial Assessment**: Upon receiving a vulnerability or weakness report, the CTI Watchdogs conduct an initial assessment to determine the severity, impact, and validity of the reported issue. This assessment helps prioritize the response and mitigation efforts.

**Validation and Verification**: The CTI Watchdogs work closely with relevant technical experts to validate and verify the reported vulnerability or weakness. This involves replicating the issue, conducting tests, and analyzing the potential impact to ensure its authenticity.

**Risk Mitigation**: Once a vulnerability or weakness is validated, the CTI Watchdogs collaborate with the appropriate stakeholders, such as developers, system administrators, or relevant project teams, to develop and implement mitigation measures. These measures aim to address the issue and minimize the associated risks effectively.

**Disclosure Planning**: The CTI Watchdogs carefully plan the disclosure process to ensure compliance with cybersecurity disclosure laws and minimize any potential risks. They consider factors such as the severity of the vulnerability, the time required for mitigation, and the potential impact on users and stakeholders.

**CTI Identifier Assignment**: During the disclosure process, the CTI Watchdogs assign a unique CTI identifier to the vulnerability or weakness. This identifier follows the CTI Identifier format (CTI-YYYY-AAA-TT-N) and serves as a standardized reference for the disclosed issue within the Cardano Threat Intelligence repository.

**CTI Template Format Disclosure**: The CTI Watchdogs disclose the vulnerability or weakness using the CTI template format, including the CTI identifier, in the CTI repository. This format ensures consistency and facilitates easy identification and reference for security researchers, developers, and blockchain experts seeking to understand and address the disclosed issue.

**Follow-up and Updates**: The CTI Watchdogs continue to monitor the situation, ensuring that the mitigation measures are effective, and actively engage with the Cardano community to address any concerns or questions related to the disclosed vulnerability or weakness. They provide updates and guidance as necessary to assist users and stakeholders in securing their Cardano deployments.

## Path to Active

### Acceptance Criteria

- The CTI has received approval from relevant stakeholders, including Cardano auditors vendors, developers, security experts, and other relevant parties involved in the Cardano ecosystem.

### Implementation Plan

- [x] The initial members of the CTI watchdogs will be selected from the Cardano Certification Working Group, which includes representation from multiple blockchain security experts, auditors, and certification issuers.

- [x] This CIP will be presented to the security and legal departments of IOG and the Cardano Foundation. The purpose is to ensure that the format and disclosure process include all the necessary information and do not pose any security or legal risks to the Cardano ecosystem as a whole.

## Copyright

This CIP is licensed under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
