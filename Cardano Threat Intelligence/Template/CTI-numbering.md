# Categorization System and Numbering Scheme

The CTI numbering system is structured as follows:

Format: CTI-YYYY-AAA-TT-N

**CTI**: Acronym for "Cardano Threat Intelligence"

**YYYY**: A four-digit year representing the discovery year of the vulnerability/weakness

**AAA**: A three-letter identifier denoting the protocol or network associated with the vulnerability/weakness (e.g., ADA for Cardano main-chain, MKD for Milkomeda side-chain, etc.)

**TT**: A two-digit combination comprising high-level category and subcategory codes that define the type of vulnerability/weakness. The initial set of categories and subcategories have been established, including on-chain, off-chain, network, and miscellaneous vulnerabilities and weaknesses. However, it is important to note that these subcategories are not fixed and can be subject to modification based on discussions among the CTI Watchdogs and other stakeholders. The CTI Watchdogs, in collaboration with the Cardano community, will evaluate the needs and requirements and make necessary adjustments to the subcategories to ensure effective categorization and organization of vulnerabilities and weaknesses.

**N**: A natural number assigned to the vulnerability/weakness within its respective category and subcategory

Some examples:

- 10: On-chain vulnerabilities
  - 01: Smart contract vulnerabilities
  - 02: Consensus mechanism vulnerabilities
    ...
- 20: Off-chain vulnerabilities
  - 01: Oracle-related vulnerabilities
  - 02: Sidechain-related vulnerabilities
    ...
- 30: Network vulnerabilities
  - 01: DDoS attack vulnerabilities
  - 02: Peer-to-peer network attack vulnerabilities
    ...
- 40: Miscellaneous vulnerabilities
- 50: On-chain weaknesses
  - 01: Smart contract weaknesses
  - 02: Consensus mechanism weaknesses
    ...
- 60: Off-chain weaknesses
  - 01: Oracle-related weaknesses
  - 02: Sidechain-related weaknesses
    ...
- 70: Network weaknesses
  - 01: DDoS attack weaknesses
  - 02: Peer-to-peer network attack weaknesses
    ...
- 80: Miscellaneous weaknesses

CTI-2021-ADA-11-1: Reentrancy vulnerability in PlutusTx smart contract  
CTI-2022-MKD-61-34: Incorrect handling of error conditions in Milkomeda oracle  
CTI-2023-ADA-31-313: DDoS attack on Cardano network