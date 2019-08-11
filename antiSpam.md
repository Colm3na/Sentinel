# Network Stress Test

![SentinelLogo](/images/sentinelLogo_transparent_small.png)

We are actually attacking the network to stress it and finding its limits.

That attack can only be done because we have miss-configured validators in the network. We would like to use this advantage before solving this issue. The solution is at the bottom and it is very easy to implement. 

[Here](https://docs.google.com/spreadsheets/d/1h8HpN3YEOJr-xd8k0jGm60B5Ne079ZRbK-JSB9UbMRU/edit?usp=sharing) in the same table we have add a new column labeled "Min-Fee". Every validator without propper minimun fee configuration and with an open RPC port is a potential gateway for a TX Spam attack like the one we are performing actually.

We are flodding the network with non sense transactions and paying no fee.

We are using [THIS SCRIPT](/scripts/spamTXs) for the attack. It would be nice to see some other validator using it to inject non sense TXs.

The effect of the Spam can be seen in the explorer in the Blocks section. The following is a snapshot of what you can see there. We have marked in yellow the blocks with a great number of TXs, what it means that the proposer is not protected against this kind of attacks.

![spamTX-picture](/images/spamTXs.png)

Once we finish with this experiment and we find the network TX limits we would like every validator to configure a minimun fee parameter this way:

<pre>
vim ~/.sentinel-hubd/config/gaiad.toml
</pre>

And add this line there:

<pre>
minimum-gas-prices = "0.001tsent"
</pre>

It is possible that this value needs to be increased in the future. We will see how the network evolve...

When a TX is broadcasted it firstly goes to a memory pool and waits for its turn to be introduced in a block. Thus, the TXs are queueing and you can check how many TX do you have in the queue with the following script:

 [THIS SCRIPT](/scripts/utx) 

You can use it without parameters to check your own validator (localhost) queue or you can check a remote node rpc using its IP as parameter.
