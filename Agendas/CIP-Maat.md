Author: Alex

# Agenda: discuss my CIP draft

TLDR: I propose to untroduce controlled randomness as a parameter and a regulable process for balancing the power of Cardano Stakeholders. I am inspired by the problem of the Summit Hackathon: transparency for governance.
So far as I understand when we talk about governance we talk about dReps most of the time. dReps are delegates, users who are able to vote on behalf of other users.

## Introduction

The problem this proposal is aiming to solve is the natural presence of Network Effects in social and collaboartive networks, described by [Barabási–Albert (BA) model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model)

First correlary is that in any human network there exist a hidden parameter which the participants get incentives to optimize for. However, the Goodheart's law states "When a measure becomes the target it ceases to be a good measure", which in this context would lead to populism. 

The hypothesis is that introducing randomness makes effort in optimizing tangible parameters less attractive, therefore fostering decentralization and egalitarian participation.

## 
In our proposal we should make distinction between two types of participant: ADA-holder and ADA-official. The first is open, and the second is gated by some process. dReps could be the current example. In our proposal each dRep gets a private mail box, to which any holder can submit feedback to. Once per each iteraction an algorithm dispenses a certain number of tokens to dReps, where number of tokens is a controlled parameter, a fraction of the whole population of the dReps.

Upon recieving the token, dReps must send it to a smart contract. From the smart contract the token can be burned.
The smart contract checks the dReps feedback mailbox and if it is empty - it allows transaction to burn the token.

If the mailbox is not empty, the dRep is registered with Transparency working group/committee, where the feedback is discussed in an open process. To burn the token in this case a multi-sig transaction has to be signed by a team formed within the Transparency WG.
Signing the transaction, each signer confirms three items:

1. I do not have objections to the consensus of the group.
2. The discussion upheld the existing norms and best practices.
3. The dREps in question may continuee as a Cardano Official.

Once the tx is signed, the token is burned and the mailbox is emptied. 

## Questions open
1. How to protect dReps from spam in the feedback box?
2. How many dReps have to be active for this CIP to make sense?
3. Does this mechanism promote transparency in governance?

https://docs.google.com/presentation/d/1J25sWk0E07WqXNWfK6GK9yEglfaDog-hnRqWQQwDerE/edit?usp=sharing

https://forum.cardano.org/t/cip-self-balancing-incentive-framework-for-dreps/121119
