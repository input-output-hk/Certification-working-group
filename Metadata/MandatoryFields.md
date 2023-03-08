## Certification mandatory fields

## General

- Subject name Subject (string)

	- Mandatory requirement: Same as registration subject. It will be used to link both together.

- Certification Level CertLevel (integer, between 1 and 3)

- Certificate issuer certificateIssuer (string, min 4 max 50 characters)

- Links to report reportURL (array of strings - urls, max 200 char-, max 10 elements)

- Hash of the report reportHash (string)

- Links to the summary of the report summaryURL (array of strings - URLs, max 200 char - max 10 elements)

- Hash of the summary of the report summaryHash (string)

- Links to the legal disclaimer disclaimerURL (array of strings - URLs, max 200 char - max 10 elements)

- Hash of the legal disclaimer disclaimerHash (string)

- On-chain script hashes scriptHashes (array of strings - hashes)

	- Shall be all the on-chain scripts of the DApp

	- Will be used to link certificates to the right DApp 

- Compilation chain used compilationChain (array of strings)

	- Compiler and version used

	- Possible post-compilation optimizations

- Tools used for verification verificationTools

	- Shall contain tool name and verison used into a standardized formal (TBD)