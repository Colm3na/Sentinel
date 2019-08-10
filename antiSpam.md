# Network Stress Test

![SentinelLogo](/images/sentinelLogo.png)

We are actually attacking the network to stress it and finding its limits.

That attack can only be done because we have miss-configured validators in the network. We would like to use this advantage before solving this issue. The solution is at the bottom and it is very easy to implement. 

[Here](https://docs.google.com/spreadsheets/d/1h8HpN3YEOJr-xd8k0jGm60B5Ne079ZRbK-JSB9UbMRU/edit?usp=sharing) in the same table we have add a new column labeled "Min-Fee". Every validator without propper minimun fee configuration and with an open RPC port is a potential gateway for a TX Spam attack like the one we are performing actually.

We are flodding the network with non sense transactions and paying no fee.

We are using [THIS SCRIPT](/scripts/spamTXs) for the attack. It would be nice to see some other validator using it to inject non sense TXs.

The effect of the Spamm can be seen in the explorer in the Blocks section. The following is a snapshot of what you can see there. We have marked in yellow the blocks with a great number of TXs, what it means that the proposer is not protected against this kind of attacks.

![spamTX-picture](/images/spamTXs.png)



