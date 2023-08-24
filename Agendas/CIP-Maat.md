Author: Alex

Agenda: discuss my CIP proposal.

The problem I would like to put forth is best described by the Cardano Summit Hackathon's theme: transparency for governance.
So far as I understand when we talk about governance we talk about dReps most of the time. dReps are delegates, users who are able to vote on behalf of other users.

So one of my goals is to encourage transparent process in governance by dReps (or any kind of official if we are facing outward - e.g. as experts building strong institutions for developing countries)

My second goal is to reduce the Price of Anarchy: the system should function at granular level, without the need for top-down control.

To solve this two issues I propose CIP-Maat: a self balancing incentive framework.

I want to utilize a private blockchain and two tokens. 
One token is native to the private blockchain and is called the proof of guilt, or the Hype token.

The second token is called the proof of shame, or the Cooldown token. It is a Cardano Native Asset.

The Cooldown token is dispensed (pseudo)-randomly to a certain fraction of the whole population of dReps. 
What it does is it shows of the users accounts, and it is in essence a warning ticket. The holder of the token is the wallet to which it was minted, and its effect is that it reduces voting power by 1/n^2, where n is the number of tokens the user has recieved.

To restore the voting power, the user must burn it through a smart contract which will infer if the number of Hype tokens the user is holding is within bounds.

Preliminary, the Hype is recieved by the user if there are complaints on their behavior. The Hype score is stored on a private blockchain only accessible via zkp. 
Remark: Self-balancing and credible reputation metrics based on well-defined inputs other than subjective ratings are needed (Gruhler et al., 2019)

To reduce the Hype score, the user must host a meeting where they will publicly reflect on their Personal Statement and on why they think their reputation has suffered. Upon consensus with other dReps their Hype is reduced and they may burn their Cooldown token. 
I suppose this will be a driver of Transparency: if a rep has recieved a Cooldown warning they must host essentially an open trial of themselves, inviting other officials to reflect with them on the happenings since their last trial.

As stated above, the incentive is progressive. Maybe it is wise to blacklist the key of a dRep who is the owner of 3 Hype tokens for 3 cycles and auction their position in the community.

The randomness of the process is supposed to counter Goodheart's law and discourage populism in dReps, and to encourage dReps to present themselves as people and act more on the grass roots and local community: act on people in their surrondings instead of being seduces by thousands of followers on social networks.

What I hope will happen is that Rich Get Richer effect will play smaller role in Cardano by introducing negative feedback on fame which is an ever present metric. My assumption is that more popular users are more likely to recieve complaints and thus will have to Cooldown and this will incentivise delegators to reassess their delegatio.

https://docs.google.com/presentation/d/1J25sWk0E07WqXNWfK6GK9yEglfaDog-hnRqWQQwDerE/edit?usp=sharing

https://forum.cardano.org/t/cip-self-balancing-incentive-framework-for-dreps/121119
