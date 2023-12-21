# CTI-YYYY-AAA-TT-N: The Vulnerability/Weakness Title

This section provides descriptive information about each component of the CTI template format used for documenting vulnerabilities and weaknesses within the Cardano Threat Intelligence (CTI) repository. It outlines the key sections included in the template and their respective purposes.

## Author

The Author section includes information about the person or team responsible for identifying the vulnerability/weakness. It specifies their names, roles, organization or company affiliation, and contact information. Additionally, any relevant certifications or qualifications held by the individuals or team may be mentioned.

## Short Summary

The Short Summary section provides a brief overview of the vulnerability/weakness finding. It includes a descriptive title that accurately summarizes the nature of the identified vulnerability/weakness.

## Description

The Description section offers a detailed account of the vulnerability/weakness, encompassing the affected system or software and the method through which it was discovered. It may include relevant background information that aids in stakeholders' understanding of the problem. The impact of the vulnerability/weakness is also described in clear and concise language.

## Risk Assessment

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

- **Severity:** This assigns a level of severity to the vulnerability or weakness based on the risk assessment. The severity levels can range from Critical to Informational. The severity levels can be defined as follows:
  - **Critical:** Vulnerabilities/Weaknesses that pose significant risks and require immediate attention and remediation.
  - **High:** Vulnerabilities/Weaknesses that can be easily exploited with a high impact.
  - **Medium:** Vulnerabilities/Weaknesses that can be exploited with some effort or have moderate impact.
  - **Low:** Vulnerabilities/Weaknesses that require significant effort to exploit or have low impact.
  - **Informational:** Vulnerabilities/Weaknesses that do not pose a significant risk by themselves but may provide useful information for attackers or reveal deficiencies in the security posture of the system.

The severity level is determined based on the combined assessment of likelihood/difficulty and impact. To provide clear guidance for severity levels, the following classification table has been created.

<table>
  <thead>
    <tr>
      <th>Likelihood</th>
      <th colspan="3">Impact</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"></td>
      <td align="center">High</td>
      <td align="center">Medium</td>
      <td align="center">Low</td>
    </tr>
    <tr>
      <td align="Left">High</td>
      <td align="center"><code>Critical</code></td>
      <td align="center"><code>High</code></td>
      <td align="center"><code>Medium</code></td>
    </tr>
    <tr>
      <td align="Left">Medium</td>
      <td align="center"><code>High</code></td>
      <td align="center"><code>Medium</code></td>
      <td align="center"><code>Low</code></td>
    </tr>
    <tr>
      <td align="Left">Low</td>
      <td align="center"><code>Medium</code></td>
      <td align="center"><code>Low</code></td>
      <td align="center"><code>Info</code></td>
    </tr>
  </tbody>
</table>

## Steps to Reproduce

The Steps to Reproduce section provides a detailed guide on how to replicate the vulnerability/weakness. It includes step-by-step instructions, relevant system environment information, and tools and tests utilized during the reproduction process.

## Technical Details

The Technical Details section encompasses additional technical information pertaining to the vulnerability/weakness. This may include details about:

- Tools used
- Methodology (methods used to identify the vulnerability/weakness)
- Affected software versions
- Smart contracts that contain vulnerable code.
- Affected and impacted system configurations
- blockchain networks utilizing smart contracts.
- Examples of vulnerable code snippets.

The section also highlights other related vulnerabilities or weaknesses, including CVE, CWE, buffer overflow, SQL injection, and any other relevant types. Moreover, it provides information about the attack vector utilized to exploit the vulnerability/weakness. The technical language used in this section is aimed at ensuring stakeholders' understanding while maintaining specificity.

## Mitigation & Remediation Steps

The Mitigation & Remediation Steps section outlines recommended actions to address and fix the vulnerability/weakness. It includes patches, software updates, system configuration changes, coding best practices, and estimated timeframes, resources, and potential implementation challenges. Workarounds to mitigate the consequences of the vulnerability/weakness while the fix is being implemented may also be suggested.

## References

The References section lists relevant sources and references consulted during the vulnerability/weakness assessment. These may include vendor advisories, known vulnerability/weakness databases, industry-standard security guidelines, and best practices.

## Tags

The Tags section allows for the inclusion of relevant keywords or labels that aid in categorizing and classifying the vulnerability or weakness described in the CTI template. These tags serve as additional metadata, helping to search and filter vulnerabilities or weaknesses based on specific criteria. They improve information discoverability and accessibility, ensuring that relevant vulnerabilities or weaknesses can be identified efficiently. Tags can include various aspects related to the vulnerability, such as related technologies, concepts, affected components, or potential impact. CTI watchdogs will establish conventions or agreed-upon keywords for adding tags, which should be concise, descriptive, and representative of the key attributes or characteristics of the vulnerability or weakness.