Author: Alex

# Agenda: discuss my CIP draft

TLDR: I propose to untroduce controlled randomness as a parameter and a regulable process for balancing the power of Cardano Stakeholders. I am inspired by the problem of the Summit Hackathon: transparency for governance.
So far as I understand when we talk about governance we talk about dReps most of the time. dReps are delegates, users who are able to vote on behalf of other users.

## Introduction

The potential problem with the dReps is not only lack of transparency, but the Network Effects. dReps that have more followers on social networks are more likely to get delegations, which is described by [Barabási–Albert (BA) model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model)

This entroduces a hidden parameter which every participant is intrinsically interested in maximizing. However, the Goodheart's law states "When a measure becomes the target it ceases to be a good measure", which in this context would lead to populism. 

## Solution

To counter this effect, I propose to introduce a process that will utilize a private blockchain and two tokens. 

One token is native to the private blockchain and is called the proof of guilt, or the Hype token.

The second token is called the proof of shame, or the Cooldown token. It is a Cardano Native Asset.

The Cooldown token is dispensed (pseudo)-randomly to a certain fraction of the whole population of dReps. 
What it does is it shows of the users accounts, and it is in essence a warning ticket. The holder of the token is the wallet to which it was minted, and its effect is that it reduces voting power by 1/n^2, where n is the number of tokens the user has recieved.

To restore the voting power, the user must burn the Cooldown token through a smart contract which will infer if the number of Hype tokens the user is holding is within bounds.

Preliminary, the Hype is recieved by the user if there are complaints on their behavior. The Hype score is stored on a private blockchain only accessible via zkp. 
Remark: Self-balancing and credible reputation metrics based on well-defined inputs other than subjective ratings are needed (Gruhler et al., 2019)

Preliminary, to reduce the Hype score, the dRep must host a meeting where they will publicly reflect on their Personal Statement and on why they think their reputation has suffered. Upon consensus with the meeting participants, a multi-sig transaction burns Hype tokens, which may or may not allow the dRep to burn their Cooldown token. 

I suppose this will be a driver of Transparency: if a rep has recieved a Cooldown warning they must host essentially an open trial of themselves, inviting other officials to reflect with them on the happenings since their last trial.

The randomness of the process is supposed to counter Goodheart's law, discourage populism and to encourage dReps to present themselves as people and act more on the grass roots and local community: act on people in their surrondings instead of being seduced by thousands of followers on social networks.

In short, we want to make more famous dReps less attractive to the voters. This is supposed to counter centralization, if there is a tendency to it.

What will happen is as a dRep becomes more famous, their Hype will grow. The only way to counter this growth is to openly reflect on recent happenings and reaffirm own's values and interests among peers. However the growth of Hype will still be impossible to stop, leading to natural slow turnover in dReps. 

As stated above, the incentive is progressive. Maybe it is wise to blacklist the key of a dRep who is the owner of N Hype tokens for K cycles and auction their position in the community.

My first goal is to encourage transparent process in governance by dReps (viewed broadly, as an of official of any kind if we are facing outward, building strong institutions for developing countries as Cardano Engineers).
My second goal is to reduce the Price of Anarchy in dReps: the system should balance itself out and be able to deviate and rebound, but ultimately stay in the state of sustainable growth.

This is the essence of CIP-Maat: a self balancing incentive framework.

## Questions open
1. Do we have a better formula for voting power multiplier then 1/n^2, where n is the number of Cooldown tokens? 
2. How many dReps have to be active for this CIP to make sense?
3. 

https://docs.google.com/presentation/d/1J25sWk0E07WqXNWfK6GK9yEglfaDog-hnRqWQQwDerE/edit?usp=sharing

https://forum.cardano.org/t/cip-self-balancing-incentive-framework-for-dreps/121119
